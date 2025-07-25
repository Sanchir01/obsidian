<%*
try {
  const res = await fetch("https://url-shortener.emgushovs.ru//api/url");
  if (!res.ok) throw new Error("HTTP " + res.status);
  const links = await res.json();
  let output = "";

  for (const link of links) {
    const shortUrl = `https://url-shortener.emgushovs.ru/${link.alias}`;
    output += `- [${shortUrl}](${link.url})\n`;
  }

  tR = output;
} catch (err) {
  tR = `**Ошибка при загрузке ссылок:** ${err.message}`;
}
%>