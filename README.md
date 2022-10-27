<!DOCTYPE html>
<html lang="en">

<head>
    </h3>
    <title>Tarefas</title>
    <style>
        #tarefas {
            align-items: center;
            background-color: rgba(219, 219, 219, 0.089);
        }

        #espaco {
            display: flex;
            justify-content: space-around;
            flex-direction: row;
            padding: 5px;
        }

        .hider{
            display: none;
        }

        .principal {
            width: 80%;
            background-color: rgb(199, 58, 58);
            border: solid 2px;
            border-color: rgb(0, 0, 0);
        }

        .itens {
            display: flex;
            justify-content: space-around;
            flex-direction: row;
            padding: 5px;
        }

        .input-group{
            justify-content: space-around;
            flex-direction: justify;
            padding: 5px;
        }

        body {
            
            background-attachment: fixed;
            background-size: 100%;
            background-image: url("agenda.jpg");
            background-repeat: no-repeat;
            background-color: rgb(0, 0, 0);
        }
    </style>
</head>

<body>
    <center>
        <div class="principal" id="d1">
            <div>        
                <h2>Login</h2>
                <div class="input-group"> 
                    Nome:
                    <input type="text" placeholder="Digite seu nome"  required>
                </div>
                <br>
                
                <div class="input-group">
                    Senha:
                    <input id="s0" minlength="8" type="password" placeholder="Digite sua senha" required>
                </div>
                <br>
                
                <div class="input-group" >
                    Confirme sua senha:
                    <input id="s1" minlength="8" type="password" placeholder="Digite sua senha"  required>
                </div>
                <br>
                <button class="btn-blue" onclick="mostrar()">Fazer Login</button>
                <br>
                <br>     
            </div>
        </div>
        <div class="hider" id="d2">
            <div class="principal">
                <br>

                <h2>MINHAS LISTAS DE COMPROMISSOS</h2>

                <h5>Digite as tarefas do dia</h5>

                <input id="texto" placeholder="Ex: Academia as 15hrs" required>

                <button onclick="adicionar()">
                    ENVIAR
                </button>

                <button onclick="limpar()">
                    LIMPAR SELECIONADOS
                </button>
                <br>
                <br>
            </div>
            <br>
            <div id="tarefas">

            </div>
        </div>
    </center>


    <script>
        var divTarefas = document.createElement('div');
        divTarefas.setAttribute("id", "tarefas");
        function adicionar() {
            var conteudo = document.getElementById('texto').value;
            if (conteudo != "") {

                var novoElemento = document.createTextNode(conteudo);
                var divNova = document.createElement('div');
                var botao = document.createElement('button');
                var box = document.createElement('input');

                //var caixa = document.createElement("input type='checkbox'");

                divNova.className = "itens";
                box.setAttribute("type", "checkbox");

                botao.innerHTML = "Remover";
                botao.addEventListener("click",
                    function () {
                        divNova.remove();
                    })
                divNova.appendChild(box);
                box.addEventListener('change', function () {
                    if (this.checked) {
                        //divNova.style.textDecoration = "line-through";
                        divNova.setAttribute("id", "espaco");
                        divNova.className = "marcados";
                    } else {
                        divNova.style.textDecoration = "none";
                    }
                })
                divNova.appendChild(novoElemento);
                divNova.appendChild(botao);
                divTarefas.appendChild(divNova);
                document.body.appendChild(divTarefas);

                document.getElementById('texto').value = "";


            }
        }

        function limpar() {

            document.getElementsByClassName('marcados')[0].remove();

        } 

        function mostrar(){
            var senha0 = document.getElementById('s0').value;
            var senha1 = document.getElementById('s1').value;
            
            var tests0 = senha0.value;
            if(length(tests0) >= 8 ){

                if( senha0 == senha1){
                    document.getElementById("d1").style.display = "none";
                    document.getElementById("d2").style.display = "inline";
                }
                else{
                    alert("senhas diferentes");
                }
            }else{
                alert("a senha contém menos de 8 caracteres");
            }
    }    
    </script>
</body>

</html>
