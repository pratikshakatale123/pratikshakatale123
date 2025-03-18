- 👋 Hi, I’m @pratikshakatale123
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
pratikshakatale123/pratikshakatale123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<html>
  <body>
    <button onclick="getNews()">Generate news</button>
    <div id="result"></div>
    <script>
      const API_KEY =
        "gsk_8ggHpUPAPRqOt4Mfe9DWWGdyb3FYxnxyTjQq8tD5NB32";


      async function getNews() {
        const response = await fetch(
          "https://api.groq.com/openai/v1/chat/completions",
          {
            method: "POST",
            headers: {
              "Content-Type": "application/json",
              Authorization: "Bearer " + API_KEY,
            },
            body: JSON.stringify({
              model: "llama-3.3-70b-versatile",
              messages: [
                {
                  role: "user",
                  content: "Generate a news only in div tag with good css",
                },
              ],
            }),
          }
        );
        const body = await response.json();
        console.log(body.choices[0].message.content);

        let newDiv = document.createElement('div');
        newDiv.innerHTML = body.choices[0].message.content;
        document.getElementById('result').appendChild(newDiv);
      }
    </script>
  </body>
</html>
