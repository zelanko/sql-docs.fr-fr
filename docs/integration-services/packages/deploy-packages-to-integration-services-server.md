---
title: "D&#233;ployer des packages sur le serveur Integration Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c26ce7f4-7b34-4c9a-8649-ba767d30c827
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# D&#233;ployer des packages sur le serveur Integration Services
  La fonctionnalité Déploiement incrémentiel de packages introduite dans  [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] vous permet de déployer un ou plusieurs packages dans un projet existant ou nouveau sans déployer la totalité du projet.  
  
##  <a name="DeployWizard"></a> Déployer des packages à l’aide de l’Assistant Déploiement d’Integration Services  
  
1.  À l’invite de commandes, exécutez **isdeploymentwizard.exe** à partir de **%ProgramFiles%\Microsoft SQL Server\130\DTS\Binn**. Sur les ordinateurs 64 bits, il existe également une version 32 bits de l’outil dans **%ProgramFiles(x86)%\Microsoft SQL Server\130\DTS\Binn**.  
  
2.  Dans la page **Sélectionner une source** , accédez à **Modèle de déploiement de package**. Ensuite, sélectionnez le dossier contenant les packages sources et configurez-les.  
  
3.  Terminez l'Assistant. Suivez le reste de la procédure décrite dans [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="SSMS"></a> Déployer des packages à l’aide de SQL Server Management Studio  
  
1.  Dans SQL Server Management Studio, développez le nœud **Catalogues Integration Services** > **SSISDB** dans l’Explorateur d’objets.  
  
2.  Cliquez avec le bouton droit sur le dossier **Projets**, puis cliquez sur **Déployer des projets**.  
  
3.  Si la page **Introduction** s’affiche, cliquez sur **Suivant** pour continuer.  
  
4.  Dans la page **Sélectionner une source** , accédez à **Modèle de déploiement de package**. Ensuite, sélectionnez le dossier contenant les packages sources et configurez-les.  
  
5.  Terminez l'Assistant. Suivez le reste de la procédure décrite dans [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="SSDT"></a> Déployer des packages à l’aide de SQL Server Data Tools (Visual Studio)  
  
1.  Dans Visual Studio, ouvrez un projet Integration Services si ce n’est déjà fait, et sélectionnez le ou les packages que vous souhaitez déployer.  
  
2.  Cliquez avec le bouton droit et sélectionnez **Déployer le package**. l’Assistant Déploiement s’ouvre avec les packages sélectionnés configurés en tant que packages sources.  
  
3.  Terminez l'Assistant. Suivez le reste de la procédure décrite dans [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel).  
  
##  <a name="StoredProcedure"></a> Déployer des packages à l’aide de la procédure stockée deploy_packages  
 Vous pouvez utiliser la procédure stockée **[catalog].[deploy_packages]** pour déployer un ou plusieurs packages SSIS dans le catalogue SSIS. l’exemple de code suivant montre comment utiliser cette procédure stockée pour déployer des packages sur un serveur SSIS. Pour plus d’informations, consultez [catalog.deploy_packages](../../integration-services/system-stored-procedures/catalog-deploy-packages.md).  
  
```  
  
private static void Main(string[] args)  
{  
    // Connection string to SSISDB  
    var connectionString = "Data Source=.;Initial Catalog=SSISDB;Integrated Security=True;MultipleActiveResultSets=false";  
  
    using (var sqlConnection = new SqlConnection(connectionString))  
    {  
        sqlConnection.Open();  
  
        var sqlCommand = new SqlCommand  
        {  
            Connection = sqlConnection,  
            CommandType = CommandType.StoredProcedure,  
            CommandText = "[catalog].[deploy_packages]"  
        };  
  
        var packageData = Encoding.UTF8.GetBytes(File.ReadAllText(@"C:\Test\Package.dtsx"));  
  
        // DataTable: name is the package name without extension and package_data is byte array of package.  
        var packageTable = new DataTable();  
        packageTable.Columns.Add("name", typeof(string));  
        packageTable.Columns.Add("package_data", typeof(byte[]));  
        packageTable.Rows.Add("Package", packageData);  
  
        // Set the destination project and folder which is named Folder and Project.  
        sqlCommand.Parameters.Add(new SqlParameter("@folder_name", SqlDbType.NVarChar, ParameterDirection.Input, "Folder", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@project_name", SqlDbType.NVarChar, ParameterDirection.Input, "Project", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@packages_table", SqlDbType.Structured, ParameterDirection.Input, packageTable, -1));  
  
        var result = sqlCommand.Parameters.Add("RetVal", SqlDbType.Int);  
        result.Direction = ParameterDirection.ReturnValue;  
  
        sqlCommand.ExecuteNonQuery();  
    }  
}  
  
```  
  
##  <a name="MOMApi"></a> Déployer des packages à l’aide de l’API Modèle d’objet de gestion  
 l’exemple de code suivant montre comment utiliser l’API Modèle d’objet de gestion pour déployer des packages sur un serveur.  
  
```  
  
static void Main()  
 {  
     // Before deploying packages, make sure the destination project exists in SSISDB.  
     var connectionString = "Data Source=.;Integrated Security=True;MultipleActiveResultSets=false";  
     var catalogName = "SSISDB";  
     var folderName = "Folder";  
     var projectName = "Project";  
  
     // Get the folder instance.  
     var sqlConnection = new SqlConnection(connectionString);  
     var store = new Microsoft.SqlServer.Management.IntegrationServices.IntegrationServices(sqlConnection);  
     var folder = store.Catalogs[catalogName].Folders[folderName];  
  
     // Key is package name without extension and value is package binaries.  
     var packageDict = new Dictionary<string, string>();  
  
     var packageData = File.ReadAllText(@"C:\Folder\Package.dtsx");  
     packageDict.Add("Package", packageData);  
  
     // Deploy package to the destination project.  
     folder.DeployPackages(projectName, packageDict);  
 }  
  
```  
  
  