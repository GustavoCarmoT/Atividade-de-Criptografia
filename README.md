# Atividade-de-Criptografia
<!DOCTYPE html>
<html>
<head>
  <title>Cifra de César</title>
</head>
<body>
  <h1>Cifra de César</h1>
  <label for="mensagem-aberta">Mensagem Aberta:</label>
  <input type="text" id="mensagem-aberta" /><br />

  <label for="mensagem-criptografada">Mensagem Criptografada:</label>
  <input type="text" id="mensagem-criptografada" /><br />

  <button onclick="criptografar()">Criptografar</button>
  <button onclick="descriptografar()">Descriptografar</button>

  <script>
    function criptografar() {
      const mensagemAberta = document.getElementById("mensagem-aberta").value;
      const chave = 3;

      let mensagemCriptografada = "";

      for (let i = 0; i < mensagemAberta.length; i++) {
        const char = mensagemAberta.charAt(i);

        if (char.match(/[a-z]/i)) {
          const codigo = mensagemAberta.charCodeAt(i);
          let novoCodigo;

          if (char.match(/[a-z]/)) {
            novoCodigo = ((codigo - 97 + chave) % 26) + 97; 
          } else {
            novoCodigo = ((codigo - 65 + chave) % 26) + 65; 
          }

          mensagemCriptografada += String.fromCharCode(novoCodigo);
        } else {
          mensagemCriptografada += char;
        }
      }

      document.getElementById("mensagem-criptografada").value = mensagemCriptografada;
    }

    function descriptografar() {
      const mensagemCriptografada = document.getElementById("mensagem-criptografada").value;
      const chave = 3;

      let mensagemAberta = "";

      for (let i = 0; i < mensagemCriptografada.length; i++) {
        const char = mensagemCriptografada.charAt(i);

        if (char.match(/[a-z]/i)) {
          const codigo = mensagemCriptografada.charCodeAt(i);
          let novoCodigo;

          if (char.match(/[a-z]/)) {
            novoCodigo = ((codigo - 97 - chave + 26) % 26) + 97; 
          } else {
            novoCodigo = ((codigo - 65 - chave + 26) % 26) + 65; 
          }

          mensagemAberta += String.fromCharCode(novoCodigo);
        } else {
          mensagemAberta += char;
        }
      }

      document.getElementById("mensagem-aberta").value = mensagemAberta;
    }
  </script>
</body>
</html>
