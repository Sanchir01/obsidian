CREATE EXTENSION IF NOT EXISTS postgres_fdw;  
DROP SERVER stat_server CASCADE;  
  
CREATE SERVER stat_server  
    FOREIGN DATA WRAPPER postgres_fdw  
    OPTIONS (host 'dbstat', dbname 'stats', port '5432');  
  
-- задаём пользователя для подключения  
CREATE USER MAPPING FOR postgres  
    SERVER stat_server  
    OPTIONS (user 'postgres', password 'sync');  
  
  
DROP USER MAPPING FOR postgres SERVER stat_server;  
  
CREATE USER MAPPING FOR postgres  
    SERVER stat_server  
    OPTIONS (user 'postgres', password 'postgres');  
  
CREATE SCHEMA IF NOT EXISTS foreign_schema;  
  
IMPORT FOREIGN SCHEMA public  
    FROM SERVER stat_server  
    INTO foreign_schema;