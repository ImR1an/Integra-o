Link:http://200.98.204.254/rreis/integracaoOutras/integracaoRian/formulario.cfm




<cfprocessingdirective pageencoding = "utf-8"/>
<!DOCTYPE html>
<cfif isDefined('hdnEnviar') and '#form.hdnEnviar#' EQ 1>
       <cfquery datasource="rreis">
           INSERT INTO integracaoRian(
               NOME
               ,SOBRENOME
               ,DATA_NASC
               ,CPF
               ,RG
               ,GENERO
               ,ESTADO_CIVIL
               ,TELEFONE
               ,EMAIL
               ,e_ndereco 
           )
           values (
               '#form.txtNome#'
               ,'#form.txtSobrenome#'
               ,'#lsDateFormat(form.dtNascimento, 'yyyy-mm-dd')#'
               ,'#form.txtCpf#'
               ,'#form.txtRg#'
               ,'#form.slcGenero#'
               ,'#form.slcEstadoCivil#'
               ,'#form.txtTelefone#'
               ,'#form.txtEmail#'
               ,'#form.txtEndereco#'
           )
       </cfquery>
</cfif>

<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>Integração</title>
<style>
		body{
			background-image: url(https://itpower.com.br/wp-content/uploads/2021/04/Ativo-1.png) ;
			background-color: black;
			background-size: 100%;
			font-family: Arial, Helvetica, sans-serif;
		}
		.box{
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%,-50%);
			background-color: rgba(54, 100, 139, 0.7);
			padding: 40px;
			padding-bottom: 50px;
			border-radius: 15px;
            width: 450px;
		}
		.campo{
			background: none;
            border: 20px;
            border-bottom: 1px solid white;
            outline: none;
            color: white;
            font-size: 15px;
            width: 100%;
            letter-spacing: 2px;
            font-size: 20px;
		}
		.titulo{
			color: darkblue;
			font-size: 30px;
			position: center;
			border-style: none;
		}
		fieldset{
            border: 3px solid dodgerblue;
        }

        .titulo{border: 1px solid dodgerblue;
            padding: 10px;
            text-align: center;
			color: black;
			font-family: sans-serif;
			background-color: rgba(99, 184, 255, 0.9);	
            border-radius: 5px;}

        input, select {

			background-color: white;
			padding: 5px;
			border-radius: 3px;
            width: 80%;
            border-width: 1.5px
        }
        #txtSobrenome{
        	width: 67%;
        }
        #txtCpf{
        	width: 83%;
		
        }
        #txtRg{
        	width: 85%;
        }
        #txtTelefone{
        	width: 71.5%;
        }
        #txtEmail{
        	width: 76%;
        }
        #txtEndereco{
        	width: 69%;

        }
        #dtNascimento{
        	width: 46%;
        }
        #slcGenero{
        	width: 75.5%;
        }

        #slcEstadoCivil{
        	width: 63.58%;
        }
        #enviar{
        	background-color: rgba(99, 184, 255, 1);	
			padding: 5px;
            width: 250px;
			height: 42px;
            text-align: center;
           position: absolute;
			left: 50%;
			transform: translate(-50%,-50%);
			border-radius: 3px;
			font-family: sans-serif;
			font-size: 25px;
			color: black;
			border-style: none;
        }

<!--- https://itpower.com.br/wp-content/uploads/2021/04/Ativo-1.png --->
	</style>
</head>
<body>
	<div class="box"> 
	<form class="form" id="formFormulario" name="formFormulario" method="post" style="margin-left: 10px, margin-right:10px">
	<input type="hidden" name="hdnEnviar" id="hdnEnviar" value="0">
		
		<legend class="titulo"><b>CADASTRO</b></legend>
		<br>
		<label for= "txtName" class="campo" >Nome:</label>
			<input type="text" name="txtNome" id="txtNome" required onkeypress="return SomenteLetras();" value="" >
		
		<br>
		<br>

		<label for= "txtSobrenome" class="campo" >Sobrenome:</label>
			<input id="txtSobrenome" type="txtSobrenome" name="txtSobrenome" required onkeypress="return SomenteLetras();" value="" >
		
		<br>
		<br>

		<label for= "Dtdata" class="campo"> Data de Nascimento:</label>
			<input type="date" name="dtNascimento" required id="dtNascimento" required value="" >
		
		<br>
		<br>


		<label for= "txtCpf" class="campo"> CPF:</label>
			<input type="text" id="txtCpf" required  value="" name="txtCpf" maxlength="14" autocomplete="off" onkeypress="formatar('###.###.###-##', this); return somenteNumeros(event);"  onBlur="ValidarCPF(this);" value="" >

		<br>
		<br>

		<label for= "txtRg" class="campo"> RG:</label>
			<input  type="text" name="txtRg" id="txtRg" maxlength="14" required  onkeypress="formatar('00.000.000-0', this); return somenteNumeros(event);" value="">
		
		<br>
		<br>

		<label for= "slcGenero" class="campo" > Gênero:
		<select   name="slcGenero" id="slcGenero" required> 

    <option value="1">Masculino</option>
    <option value="2" selected>Feminino</option>
    <option value="3">Outro</option>
    </select>
        </label>
        <br>
        <br>

        <label for= "telTelefone" class="campo" required> Telefone: </label>
			<input  type="text" name="txtTelefone" id="txtTelefone" maxlength="14" onkeypress="formatar('00 0000-0000', this) ;return somenteNumeros(event);" value="" required >

		<br>
		<br>

		<label for= "e-mail" class="campo" > E-mail: </label>
			<input  required type="e-mail" name="txtEmail" id="txtEmail" onkeypress="return SomenteEmail();" onblur="ValidaEmail(this);" value=""required>
		

		<br>
		<br>

		<label for= "slcEstadoCivil" class="campo">Estado Cívil:
		<select name="slcEstadoCivil" id="slcEstadoCivil">
    <option value="1">Solteiro(a)</option>
    <option value="2" selected>Casado(a)</option>
    <option value="3">Viuvo(a)</option>
    </select>
        </label>
        <br>
        <br>

        <label required for= "endereço" class="campo"> Endereço:
        	<input  type="text" name="txtEndereco" id="txtEndereco" value="">
        </label>
        <br>
        <br>
        <br>
		<br>
     
        <button id="enviar" type="submit" onSubmit="enviaDados();"><b>Enviar</b></button>
</div>
<br>
<br>
	</form>

	<script type="text/javascript">
    // function Inseredados() {
    //     document.getElementById("hdnInseredados").value = 1
    //     document.getElementById("formFormulario").submit()
        
    // }

		//Função somente números----------------------
		function somenteNumeros(e) {
		var charCode = e.charCode ? e.charCode : e.keyCode;
		// charCode 8 = backspace   
		// charCode 9 = tab
		if (charCode != 8 && charCode != 9) {
		// charCode 48 equivale a 0   
		// charCode 57 equivale a 9
		if (charCode < 48 || charCode > 57) {
		return false;
		}
		}
		}
		
		
		  //Função somente letras com espaço----------------------
		function SomenteLetras(){
		var tecla=(window.event)?event.keyCode:e.which;   
		if((tecla>64 && tecla<91)) return true;
		else{
		if (tecla>96 && tecla<123 || tecla==32) return true;
		else  return false;
		}
		
		}
		
		
		//função somente caracteres de email----------------------
		function SomenteEmail(){
		var tecla=(window.event)?event.keyCode:e.which;   
		if((tecla>63 && tecla<91 || tecla==46)) return true;
		else{
		if (tecla>96 && tecla<123 || tecla==95) return true;
		else{
		if (tecla>47 && tecla<58) return true;
		else
		return false;
		}
		}
		}
		
		//Função para validar CPF----------------------
		function ValidarCPF (input) {
		s = input.value;
		filteredValues = ".-/"; 
		var i;
		var returnString = "";
		for (i = 0; i < s.length; i++) { 
		var c = s.charAt(i);
		if (filteredValues.indexOf(c) == -1) returnString += c;
		}
		if (returnString=='11111111111' || returnString=='22222222222' || 
		returnString=='33333333333' || returnString=='44444444444' || 
		returnString=='55555555555' || returnString=='66666666666' || 
		returnString=='77777777777' || returnString=='88888888888' || 
		returnString=='99999999999' || returnString=='00000000000' || returnString=='00000000191')
		{alert('CFP Inválido!'); input.value=""; return false;}
		if (returnString.length != 11) {sim=false}
		else {sim=true}
		if (sim ) {
		for (i=0;((i<=(returnString.length-1))&& sim); i++) {
		val = returnString.charAt(i)
		if ((val!="9")&&(val!="0")&&(val!="1")&&(val!="2")&&(val!="3")&&(val!="4")
		&& (val!="5")&&(val!="6")&&(val!="7")&&(val!="8")) {sim=false}
		}
		if (sim) {
		soma = 0
		for (i=0;i<=8;i++) {
		val = eval(returnString.charAt(i))
		soma = soma + (val*(i+1))
		}
		resto = soma % 11
		if (resto>9) dig = resto -10
		else  dig = resto
		if (dig != eval(returnString.charAt(9))) { sim=false }
		else { 
		soma = 0
		for (i=0;i<=7;i++) {
		val = eval(returnString.charAt(i+1))
		soma = soma + (val*(i+1))
		}
		soma = soma + (dig * 9)
		resto = soma % 11
		if (resto>9) dig = resto -10
		else  dig = resto
		if (dig != eval(returnString.charAt(10))) { sim = false }
		else {sim = true;}
		}
		}
		}
		
		if (sim != true) {
		if (input.value != ''){
		alert("CPF Inválido!");
		input.value = '';
		return false;
		}
		else{
		return false;  
		}	 
		}
		}
		
		
		//Função para formatar mascara----------------------
		function formatar(mascara, documento){
		var i = documento.value.length;
		var saida = mascara.substring(0,1);
		var texto = mascara.substring(i)
		
		if (texto.substring(0,1) != saida){
		documento.value += texto.substring(0,1);
		
		}
		}

		//Função para validar e-mail
		function ValidaEmail(campo) {
    if (campo.value != '' && campo.value != null) {
        var f = campo.value
        if ((f.indexOf("@") == -1) || (f.indexOf(".") == -1) && (f != '')) {
            window.alert('Email invalido');
            campo.focus();
            campo.value = '';
        }
    }
}
		
		//Criar Formulário com os campos(Nome, Sobrenome, Data de Nascimento, CPF, RG, Gênero, Telefone, e-mail, Estado civil e Endereço)------------ 
		
		</script>

		<script>
		//Função enviar dados
		function enviaDados() {
		document.querySelector('#hdnEnviar').value = 1;
        document.querySelector("#formFormulario").submit();
        
		}
		</script>
</body>
</html>

<!--- Retona total de registros na tabela --->





