<h1>Implementation of authentication and authorization mechanisms on Helix Sandbox-NG Platform</h1>
<h3>Project contributors:</h3>
<p>This project was developed by the students <a  href="https://www.fatecsaocaetano.edu.br/" target="_blank">, as an undergraduate project guided by <a  href="http://lattes.cnpq.br/3044213933175294" target="_blank">Professor Me. Fábio Henrique Cabrini</a>.</p>
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
