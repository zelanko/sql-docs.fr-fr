1. **Sur tous les serveurs SQL Server, créez un compte de connexion Server pour Pacemaker**. Le code Transact-SQL ci-dessous a pour effet de créer un compte de connexion :

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

   Vous pouvez aussi définir les autorisations à un niveau plus granulaire. Le compte de connexion Pacemaker nécessite ALTER, CONTROL et VIEW DEFINITION PERMISSION. Pour plus d’informations, consultez [GRANT (Octroi d’autorisations de groupe de disponibilité) (Transact-SQL)](http://msdn.microsoft.com/library/hh968934.aspx).

   Le code Transact-SQL ci-dessous ne fait qu’accorder l’autorisation nécessaire au compte de connexion Pacemaker. Dans l’instruction ci-dessous, « ag1 » est le nom du groupe de disponibilité qui sera ajouté comme ressource de cluster.

   ```Transact-SQL
   GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO pacemakerLogin
   ```

1. **Sur tous les serveurs SQL Server, enregistrez les informations d’identification pour le compte de connexion SQL Server**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
