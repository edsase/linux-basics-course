# SSH and SCP

  - Take me to the [Tutorial](https://kodekloud.com/courses/873064/lectures/17074517)
  - In this lecture we will learn about SSH and SCP commands.
  - SSH is used to login to the remote computer.
  - SCP is used to copy of files/directories within the file system also can copy data to remote computer.

  #### SSH

  - To login to the remote server use **`ssh`** command with hostname or IP address.

    ```
    ssh <hostname OR IP Address>
    ```

  - To login to the remote server with specific username and password.

    ```
    ssh <user>@<hostname OR IP Address>
    ```

    **`-l`** attribute can also be used as 

    ```
    ssh –l <user> <hostname OR IP Address>
    ```

  #### Password-Less Authentication

  - Passwordless authentication can be setup via key-pair authentication in order to login to the remote server with password.

  - Public and Private key are stored at below location.
    
    ```
    Public Key: /home/bob/.ssh/id_rsa.pub
    ```

    ```
    Private Key: /home/bob/.ssh/id_rsa
    ```

  - To generate a keypair on the **`Client`** run this command

    ```
    bob@caleston-lp10 ~]$ ssh-keygen –t rsa
    ```

    ![key](../../images//key.PNG)

  - To copy the Public key from the client to the remote server

    ```
    bob@caleston-lp10 ~]$ ssh-copy-id bob@devapp01
    ```

    ![copy](../../images//copy.PNG)

 
  - Now **`Bob`** can login to remote server without password

    ```
    [bob@caleston-lp10 ~]$ ssh devapp01
    ```

    ![pless](../../images//pless.PNG)

  - Public Key is copied to the remote server at :

    ```
    [bob@caleston-lp10 ~]$ cat /home/bob/.ssh/authorized_keys
    ```
   
    ![auth](../../images//auth.PNG)
    

  #### SSH Local Port Forwarding
   - Run a simple SSH command with port forwarding to forward a local port to a remote local connection. When you run an SSH port-forwarding command like -L 8111:127.0.0.1:8888, you are telling SSH to forward your local port 8111 to what the remote host thinks 127.0.0.1:8888 is. The remote host thinks 127.0.0.1 is itself.
   ```
   $ ssh -L 8111:127.0.0.1:8888 edsase@192.168.0.136
   ```
   - The above will allow whatever resource running on 192.168.0.136:8888 to be forwarded to localhost:8111
  
  #### SCP

   - To copy a compresses file to a remote server

     ```
     bob@caleston-lp10 ~]$ scp /home/bob/caleston-code.tar.gz devapp01:/home/bob
     ```
 
   - To copy a directory to a remote server

     ```
     [bob@caleston-lp10 ~]$ scp –pr /home/bob/media/ devapp01:/home/bob
     ```
     
     ![scp](../../images//scp.PNG)
