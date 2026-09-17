<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Parabéns, você vendeu!</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
  min-height:100vh;
  font-family:Arial,Helvetica,sans-serif;
  color:#fff;
  overflow-x:hidden;
  background:linear-gradient(120deg,#6d28d9,#f97316,#22c55e,#6d28d9);
  background-size:400% 400%;
  animation:cores 8s ease infinite;
}

@keyframes cores{
  0%{background-position:0% 50%}
  50%{background-position:100% 50%}
  100%{background-position:0% 50%}
}

.page{
  min-height:100vh;
  display:none;
  align-items:center;
  justify-content:center;
  padding:25px;
}

.page.active{
  display:flex;
}

.card{
  width:100%;
  max-width:520px;
  padding:40px 30px;
  text-align:center;
  background:rgba(0,0,0,.25);
  border:1px solid rgba(255,255,255,.3);
  border-radius:25px;
  backdrop-filter:blur(15px);
  box-shadow:0 25px 70px rgba(0,0,0,.25);
}

.logo{
  font-size:18px;
  font-weight:bold;
  margin-bottom:25px;
  opacity:.9;
}

h1{
  font-size:clamp(38px,9vw,62px);
  line-height:1.05;
  margin-bottom:18px;
}

h2{
  font-size:32px;
  margin-bottom:12px;
}

p{
  font-size:17px;
  line-height:1.6;
  color:#f1f5f9;
  margin-bottom:28px;
}

.btn{
  width:100%;
  border:0;
  padding:16px 20px;
  margin-top:10px;
  border-radius:12px;
  font-size:17px;
  font-weight:bold;
  cursor:pointer;
  transition:.25s;
}

.btn:hover{
  transform:translateY(-2px);
}

.btn-primary{
  background:#fff;
  color:#4c1d95;
}

.btn-green{
  background:#22c55e;
  color:#fff;
}

.btn-orange{
  background:#f97316;
  color:#fff;
}

.btn-back{
  background:rgba(255,255,255,.15);
  color:#fff;
}

.form{
  text-align:left;
  margin-top:25px;
}

.form-group{
  margin-bottom:18px;
}

label{
  display:block;
  margin-bottom:7px;
  font-weight:bold;
}

input,select{
  width:100%;
  padding:15px;
  border:0;
  outline:none;
  border-radius:10px;
  font-size:16px;
}

input:focus,select:focus{
  box-shadow:0 0 0 3px rgba(255,255,255,.35);
}

.info{
  background:rgba(255,255,255,.1);
  padding:14px;
  border-radius:10px;
  margin-top:18px;
  font-size:13px;
  color:#e2e8f0;
}

.success{
  font-size:55px;
  margin-bottom:15px;
}

.hidden{
  display:none;
}

.small{
  font-size:13px;
  opacity:.8;
  margin-top:18px;
  margin-bottom:0;
}

@media(max-width:500px){
  .card{
    padding:32px 20px;
  }

  h1{
    font-size:42px;
  }

  h2{
    font-size:28px;
  }
}
</style>
</head>

<body>

<!-- =========================
     PÁGINA 1
========================= -->

<section class="page active" id="inicio">

  <div class="card">

    <div class="logo">
      SEU SITE
    </div>

    <h1>
      Parabéns,<br>
      você vendeu! 🎉
    </h1>

    <p>
      Sua venda foi concluída. Agora siga para o próximo passo
      para informar os dados necessários para o atendimento.
    </p>

    <button
      class="btn btn-primary"
      onclick="mostrarPagina('dados')">
      Seguir para o próximo passo →
    </button>

  </div>

</section>


<!-- =========================
     PÁGINA 2
========================= -->

<section class="page" id="dados">

  <div class="card">

    <div class="logo">
      PRÓXIMO PASSO
    </div>

    <h2>Informe seus dados</h2>

    <p>
      Preencha os campos abaixo para continuar.
    </p>

    <form class="form" id="dadosForm">

      <div class="form-group">

        <label for="pix">
          Chave Pix
        </label>

        <input
          type="text"
          id="pix"
          placeholder="Digite sua chave Pix"
          autocomplete="off"
          required>

      </div>


      <div class="form-group">

        <label for="nome">
          Nome completo
        </label>

        <input
          type="text"
          id="nome"
          placeholder="Digite seu nome completo"
          autocomplete="name"
          required>

      </div>


      <div class="form-group">

        <label for="banco">
          Nome do banco
        </label>

        <input
          type="text"
          id="banco"
          placeholder="Digite o nome do banco"
          required>

      </div>


      <button
        type="submit"
        class="btn btn-green">
        Continuar →
      </button>

      <button
        type="button"
        class="btn btn-back"
        onclick="mostrarPagina('inicio')">
        ← Voltar
      </button>

    </form>

    <div class="info">
      🔒 Seus dados devem ser tratados de acordo com as
      regras de privacidade aplicáveis.
    </div>

  </div>

</section>


<!-- =========================
     PÁGINA 3
========================= -->

<section class="page" id="whatsapp">

  <div class="card">

    <div class="success">
      ✓
    </div>

    <h2>
      Dados preenchidos!
    </h2>

    <p>
      Para continuar o atendimento, clique no botão abaixo
      para falar conosco pelo WhatsApp.
    </p>

    <button
      class="btn btn-green"
      onclick="abrirWhatsApp()">
      💬 Falar no WhatsApp
    </button>

    <button
      class="btn btn-back"
      onclick="mostrarPagina('dados')">
      ← Voltar e revisar dados
    </button>

    <p class="small">
      Você poderá enviar os detalhes necessários diretamente
      na conversa.
    </p>

  </div>

</section>


<script>

/* =========================================
   CONFIGURAÇÃO DO WHATSAPP
   =========================================

   COLOQUE O NÚMERO DO DONO DO SITE AQUI.

   Formato:
   55 + DDD + número

   Exemplo:
   5587999999999

   Não coloque:
   +
   espaços
   parênteses
   hífen
========================================= */

const NUMERO_WHATSAPP = "5587999999999";


/* =========================================
   NAVEGAÇÃO ENTRE AS PÁGINAS
========================================= */

function mostrarPagina(id){

  document.querySelectorAll(".page").forEach(function(page){

    page.classList.remove("active");

  });

  document.getElementById(id).classList.add("active");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });
}


/* =========================================
   FORMULÁRIO
========================================= */

document
.getElementById("dadosForm")
.addEventListener("submit",function(event){

  event.preventDefault();

  const pix =
    document.getElementById("pix").value.trim();

  const nome =
    document.getElementById("nome").value.trim();

  const banco =
    document.getElementById("banco").value.trim();


  if(!pix || !nome || !banco){

    alert("Preencha todos os campos.");

    return;
  }


  /*
    Os dados ficam apenas nesta página.
    Não são enviados automaticamente para terceiros.
  */

  sessionStorage.setItem(
    "nomeCliente",
    nome
  );

  mostrarPagina("whatsapp");

});


/* =========================================
   WHATSAPP
========================================= */

function abrirWhatsApp(){

  const mensagem =
    "Olá! Gostaria de continuar meu atendimento.";

  const url =
    "https://wa.me/" +
    NUMERO_WHATSAPP +
    "?text=" +
    encodeURIComponent(mensagem);

  window.open(
    url,
    "_blank",
    "noopener,noreferrer"
  );
}

</script>

</body>
</html>
