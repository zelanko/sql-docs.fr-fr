1. **Sur tous les serveurs SQL Server, créez un compte de connexion Server pour Pacemaker**. Le code Transact-SQL ci-dessous a pour effet de créer un compte de connexion :

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

   Vous pouvez aussi définir les autorisations à un niveau plus granulaire. Le compte de connexion Pacemaker nécessite l’autorisation ALTER, CONTROL et VIEW DEFINITION pour gérer le groupe de disponibilité, et l’autorisation VIEW SERVER STATE pour pouvoir exécuter sp_server_diagnostics. Pour plus d’informations, consultez [GRANT Availability Group Permissions (Transact-SQL)](http://msdn.microsoft.com/library/hh968934.aspx) (Accorder des autorisations de groupe de disponibilité [Transact-SQL]) et [sp_server_diagnostic permissions](https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql#permissions) (autorisations sp_server_diagnostic).

   Le code Transact-SQL ci-dessous ne fait qu’accorder l’autorisation nécessaire au compte de connexion Pacemaker. Dans l’instruction ci-dessous, « ag1 » est le nom du groupe de disponibilité qui sera ajouté comme ressource de cluster.

   ```Transact-SQL
   GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO pacemakerLogin
   GRANT VIEW SERVER STATE TO pacemakerLogin
   ```

1. **Sur tous les serveurs SQL Server, enregistrez les informations d’identification pour le compte de connexion SQL Server**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
