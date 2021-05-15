<h1>Implementation of authentication and authorization mechanisms on Helix Sandbox-NG Platform</h1>
<p>Versão em Português: <a href="https://github.com/felipe-mcunha/arquitetura-seguranca">Implementação dos mecanismos de autenticação e autorização na Plataforma Helix Sandbox-NG</a></p>
<h3>Project contributors:</h3>
<p>This project was developed by the students of <a  href="https://www.fatecsaocaetano.edu.br/" target="_blank">Fatec São Caetano do Sul</a>, as an undergraduate project guided by <a  href="http://lattes.cnpq.br/3044213933175294" target="_blank">Professor Me. Fábio Henrique Cabrini</a>.</p>
<ul>
  <li><a  href="https://www.linkedin.com/in/felipe-cunha-7aa33935/" target="_blank">Felipe Matheus da Cunha</a></li>
  <li><a  href="https://www.linkedin.com/in/jo%C3%A3o-vitor-ara%C3%BAjo-bonfim-7406b619b/" target="_blank">João Vitor de Araujo Bonfim</a></li>
  <li><a  href="https://www.linkedin.com/in/matheus-pereira-mendes-900269192/" target="_blank">Matheus Pereira Mendes</a></li>
  <li><a  href="https://www.linkedin.com/in/fabio-cabrini/" target="_blank">Fábio Henrique Cabrini</a></li>
</ul>  
<h3>Project description:</h3>
<p>The architecture presented performs the implementation of FIWARE security solutions without the need for changes in the helix platform structure, where the user now has access to visualize the operation of Context Broker, but when performing the creation of entities in the Context broker it is necessary to authenticate in the environment.‎</p>
  <p>Previously the IoT device when communicating with the platform to make changes, had a direct communication with Context Broker occurred without the need for authentication, after deployment, the device begins to authenticate to read of existing information in the database, write new information on the database, or change existing information.‎</p>
  <p>For the elaboration of the architecture were used three FIWARE solutions, which are: Pep-proxy, AuthzForce, and Wilma Pep-Proxy, each responsible for a step in the system. Keyrock is an identity manager, where the identities that will be registered in Helix must be created to receive authorization in the environment, along with the account of administrators who will make changes to the environment. Authzforce is a Policy decision point (PDP) that will make decisions based on previously created policies. And finally, the Wilma Pep-Proxy which is a PEP (Policy enforcement point) that will have the function of intercepting traffic and consulting the Authzforce and Keyrcok to identify if the device that is trying to communicate with the context broker is authorized to perform the connection, and permission to perform actions on the Helix platform.‎</p>
  <img src="https://user-images.githubusercontent.com/70486745/117086554-3768ae80-ad23-11eb-8cb2-30b9584b6bd9.jpg">
<h3>Step by step:</h3>

<p><h4>Step 1 - The first step to install the architecture is to download the files contained in GitHub</h4>

 To get the files type the command:
 <ul>
  <li>git clone https://github.com/m-mendes/security-architecture.git</li>
  <li>cd security-architecture</li>
</ul>
 </p> 



<p><h4>Step 2 - We need to download the security files, if you have the helix installed, we will use the requirements.sh file, if it is necessary the installation of helix will need to use the file requirements_without_helix.sh</h4>

To get the files type the command:
 <ul>
  <li>sudo chmod 777 requirements.sh ou requirements_without_helix.sh</li>
  <li>./requirements.sh ou requirements_without_helix.sh</li> 
</ul>
 </p> 

<p><h4>Step 3 - If you already have helix installed and have activated Context Broker skip to step 4</h4>
  <h4>For those who dosn't have already, follow helix's GitHub walkthrough to activate Context Broker
<a href="https://github.com/Helix-Platform/Sandbox-NG/blob/master/docs/create_cef_context_broker.md">Creating a CEF Context Broker</a></h4>
<h4>To validate the connection follow the following walkthrough:</h4>
<p> Copy the file creating_entity_on_helix to the notebook and change the IP
<h3>Youtube link to perform the first step </h3>
https://www.youtube.com/watch?v=CEI9_HaFaBQ
</p>

<p><h4>Step 4 - In this step we will climb the first security tool, the Authzforce, Follow the commands below:</h4>
<ul>
  <li>cd authzforce</li>
  <li>docker-compose up</li>
  <li>Wait for the container process to be activated</li>
  <li> Press CTRL + Z and then bg to play the application in 2nd plan</li>
  <li>Return to the security architecture folder using the command cd..</li>
</ul>

</p>

<p>
  <h4>Step 5 - In this step will be configured the second security tool, keyrock, Follow the commands below:</h4>
<ul>
  <li>cd keyrock</li>
  <li>nano docker-compose.yml - It will be necessary to set up AuthzForce IP</li>
  <li>On line 31 contain: <strong>IDM_AUTHZFORCE_HOST={IP HOST}</strong> </li>
  <li>Replace <stron>{IP HOST} for</stron> the ip where Authzforce will be configured the same in the following image:</li>
  <img src="https://user-images.githubusercontent.com/70486745/117071816-fada8a00-ad05-11eb-8e05-f205df9394ff.PNG">

  <li>Save the file: ctrl+O > ENTER > ctrl X</li>
  <li>docker-compose up to activate the Keyrock container</li>
  <li>Wait for the container process to be activated</li>
  <li>After installation open a new putty terminal, enter as root and access the architecture-security folder</li>
</ul>
</p>

<p>
  <h4>Step 6 - Now we need to create an entity in keyrock, because to perform the configuration of Wilma it will be necessary to get an access token, generated in the keyrock. Follow the steps below:</h4>
  <ul>
    <li>The first step is to log into the keyrock using the browser, typing the IP of the machine :3000</li>
    <li>Sign in user: admin@test.com and password: 1234</li>
    <li>Follow the images below to get the necessary tokens</li>

  </ul>
  <img src="https://user-images.githubusercontent.com/70486745/117065150-7b48bd00-acfd-11eb-98b0-2922dfc977c3.PNG">
  <img src="https://user-images.githubusercontent.com/70486745/117065658-25c0e000-acfe-11eb-8c8a-33664598c399.PNG">
  <img src="https://user-images.githubusercontent.com/70486745/117066516-332a9a00-acff-11eb-9a7f-cdb483ec5c02.PNG">
  <img src="https://user-images.githubusercontent.com/70486745/117067012-daa7cc80-acff-11eb-900f-ba50eb7486e5.jpg">
  <img src="https://user-images.githubusercontent.com/70486745/117067620-a2ed5480-ad00-11eb-9a95-80e19c928550.PNG">
  <img src="https://user-images.githubusercontent.com/70486745/117068088-345cc680-ad01-11eb-995b-5690c9a5fd52.PNG">
  <h4>Save tokens in notepad, they will be used in step 7</h4>


</p>


<p><h4>Step 7 - Now we will perform the activation and configuration of Wilma, Follow the step by step below:</h4></p>
<ul>
  <li>cd wilma</li>
  <li>Enter the command to create the container image: docker build -t pep-proxy-image . (Note: </strong>do not remove the point and space</strong>) </li>
  <li>Then type the command nano config.js</li>
  <li>On line 15 inform the IP of the machine that the keyrock is active.</li>
  <li>On line 21 inform the IP that the context broker is active.</li>
  <li>On line 33, 34 and 35 you will be informed of the credentials generated in keyrock in the previous step.</li>
  <img src="https://user-images.githubusercontent.com/70486745/117068954-45f29e00-ad02-11eb-905c-2a207dfb9689.PNG">
  <li>On line 58 inform the IP that Authzforce is active.</li>
  <li>Save the file: CTRL+O > ENTER > CTRL X</li>
  <li>Note: Get the path with the PWD command and paste in the command below in the field {PATH}</li>
  <li>sudo docker run -d --name pep-proxy-container -v <strong>{PATH}</strong>/arquitetura-seguranca/wilma/config.js:/opt/fiware-pep-proxy/config.js -p 1027:1027 pep-proxy-image</li>
  <li>Wait for the process to finish, and after that the 4 tools will be connected.</li>
</ul>
<h3>Youtube link to perform the second stage</h3>
https://www.youtube.com/watch?v=aTkyHVxOqCo&feature=youtu.be


<p>


</p>


<p>Step 8 - Now we will get the Keyrock access token, follow the following images to get the APP ID and SECRET ID:<h4></h4></p>
<img src="https://user-images.githubusercontent.com/70486745/117069768-47709600-ad03-11eb-85c3-f8a522b7e6da.PNG">
<img src="https://user-images.githubusercontent.com/70486745/117070473-28263880-ad04-11eb-9804-3eeff16f4fd3.PNG">
With these tokens in hand we will generate a base64 to request the access token  to the keyrock. use the echo below by changing the APP ID and SECRET that was obtained<br><br>

<h4><strong>Note: Use the file validation, contained in the repositorio to do the tests</strong></h4>

echo -n <strong>{APP_ID}</strong>:<strong>{SECRET}</strong> | base64><br>

Copy the command below, in the base64 option change for the response from the echo command, and change to the IP of the machine that Keyrock is installed.<br><br>
curl -iX POST \ <br>
'http://<strong>{IP}</strong>:3000/oauth2/token' \ <br>
-H 'Accept: application/json' \ <br>
-H 'Authorization: Basic <strong>{BASE64}</strong>' \ <br>
-H 'Content-Type: application/x-www-form-urlencoded' \ <br>
--data "username=admin@test.com&password=1234&grant_type=password" <br>
<br><br>


  Now we will check if the tools are connected, from the following command, the answer that it should return us is that domain does not exist, inform the access token obtained in the previous command:<br><br>


curl --location --request GET 'http://<strong>{IP}</strong>:1027/v2/entities' \ <br>
--header 'Accept: application/json' \ <br>
--header 'fiware-service: helixiot' \ <br>
--header 'fiware-servicepath: /' \ <br>
--header 'X-Auth-Token: <strong>{ACCESS TOKEN}</strong>'<br>
<br>
<h4>As a test to check whether Authzforce is receiving rules from keyrock, follow the next step by step to create the rule in Keyrock and it re-passes authzforce</h4>
<img src="https://user-images.githubusercontent.com/70486745/117084099-a7c00180-ad1c-11eb-824a-56e15fd210d3.png">
<img src="https://user-images.githubusercontent.com/70486745/117084359-63813100-ad1d-11eb-9d3f-b32430dadd13.png">
<img src="https://user-images.githubusercontent.com/70486745/117084609-02a62880-ad1e-11eb-9077-392ac54f737e.PNG">
<img src="https://user-images.githubusercontent.com/70486745/117084763-721c1800-ad1e-11eb-9d61-c64644a5873f.PNG">
<p>In this step we will create the rule in Keyrock to be transmitted to Authzforce, Enter the name of the rule, a description and the XACML code used in the example that is available in the file access_rule.xacml</p>
<h5>Note: You will need to edit the Client ID of the XACML file on line 25</h5>
<img src="https://user-images.githubusercontent.com/70486745/117085697-d8099f00-ad20-11eb-979c-3f70e051ccff.PNG">
<img src="https://user-images.githubusercontent.com/70486745/117085858-56fed780-ad21-11eb-8aff-85a48410756c.png">
<img src="https://user-images.githubusercontent.com/70486745/117086043-dd1b1e00-ad21-11eb-8079-6b0bd7502a57.png">
<p>After clicking save, Authzforce will already receive and create the domain for the entity.</p>
<h5>Validation of the reading rule</h5>
<p>Resubmit the command used in the previous step for connection validation, the expected return should be the information in the helix entity.</p>
curl --location --request GET 'http://<strong>{IP}</strong>:1027/v2/entities' \ <br>
--header 'Accept: application/json' \ <br>
--header 'fiware-service: helixiot' \ <br>
--header 'fiware-servicepath: /' \ <br>
--header 'X-Auth-Token: <strong>{ACCESS TOKEN}</strong>'<br>
<br>
<h3>Youtube link to perform the third stage: </h3>
https://www.youtube.com/watch?v=qBaY3kxcSf8
