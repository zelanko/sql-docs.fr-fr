---
description: 'Tutoriel : Développer une application .NET Framework avec Always Encrypted avec enclaves sécurisées'
title: 'Tutoriel : Développer une application .NET Framework avec Always Encrypted avec enclaves sécurisées | Microsoft Docs'
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: cd75e0a63ebbfbf6a5749939442b8b8a2e964d92
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88403795"
---
# <a name="tutorial-develop-a-net-framework-application-using-always-encrypted-with-secure-enclaves"></a>Tutoriel : Développer une application .NET Framework avec Always Encrypted avec enclaves sécurisées
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Ce tutoriel vous apprend à développer une application simple qui émet des requêtes de base de données utilisant une enclave sécurisée côté serveur pour [Always Encrypted avec enclaves sécurisées](encryption/always-encrypted-enclaves.md). 

## <a name="prerequisites"></a>Prérequis
Ce didacticiel est la continuation du [Didacticiel : Prise en main d’Always Encrypted avec enclaves sécurisées en utilisant SSMS](./tutorial-getting-started-with-always-encrypted-enclaves.md). Assurez-vous que vous avez terminé, avant de suivre les étapes ci-dessous.

Par ailleurs, vous devez avoir Visual Studio (version 2019 recommandée), que vous pouvez télécharger depuis [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com). Votre ordinateur de développement d’applications doit exécuter .NET Framework 4.7.2 ou ultérieur.

## <a name="step-1-set-up-your-visual-studio-project"></a>Étape 1 : Configurez votre projet Visual Studio

Pour utiliser Always Encrypted avec enclaves sécurisées dans une application .NET Framework, vous devez vérifier que votre application repose sur .NET Framework 4.7.2 et qu’elle est intégrée au package NuGet [Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders). En outre, si vous stockez votre clé principale de colonne dans Azure Key Vault, vous devez également intégrer votre application au package NuGet [Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider) version 2.2.0 ou ultérieure. 

1. Ouvrez Visual Studio.

2. Créez un projet (.NET Framework) d’application console C\#.

3. Assurez-vous que votre projet cible au moins .NET Framework 4.7.2. Cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, sélectionnez Propriétés et définissez l’infrastructure cible sur .NET Framework 4.7.2.

4. Installez le package NuGet suivant en accédant à **Outils** (menu principal) > **Gestionnaire de Package NuGet** > **Console du gestionnaire de package**. Exécutez le code suivant dans la Console du gestionnaire de Package.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders -IncludePrerelease
   ```

5. Si vous utilisez Azure Key Vault pour stocker vos clés principales de colonne, installez les packages NuGet suivants en accédant à **Outils** (menu principal) > **Gestionnaire de package NuGet** > **Console de gestionnaire de package**. Exécutez le code suivant dans la Console du gestionnaire de Package.

   ```powershell
   Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider -IncludePrerelease -Version 2.2.0
   Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
   ```

7. Ouvrez le fichier App.config pour votre projet.

8. Recherchez la section \<configuration\>, et ajoutez ou mettez à jour les sections \<configSections\>.

   a. Si la section \<configuration\> ne contient **pas** de section \<configSections\>, ajoutez le contenu suivant juste en dessous de \<configuration\>.
   
      ```xml
      <configSections>
         <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
      </configSections>
      ```
   b. Si la section \<configruation\> contient déjà la section \<configSections\>, ajoutez la ligne suivante dans \<configSections\> :

   ```xml
   <section name="SqlColumnEncryptionEnclaveProviders"  type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data,  Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
   ```

9. À l’intérieur de la section configuration, sous \<configSections\>, ajoutez la section suivante, qui spécifie un fournisseur d’enclave à utiliser pour attester et interagir avec les enclaves VBS :

   ```xml
   <SqlColumnEncryptionEnclaveProviders>
       <providers>
           <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
       </providers>
   </SqlColumnEncryptionEnclaveProviders>
   ```

Voici un exemple complet de fichier app.config pour une application console simple.
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="VBS"  type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.HostGuardianServiceEnclaveProvider,  Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,    Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/>
    </providers>
  </SqlColumnEncryptionEnclaveProviders>
  <startup> 
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.2" />
  </startup>
</configuration>
```
## <a name="step-2-implement-your-application-logic"></a>Étape 2 : Implémentez votre logique d’application
Votre application se connecte à la base de données **ContosoHR** à partir du [Tutoriel : Bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](tutorial-getting-started-with-always-encrypted-enclaves.md) et exécute une requête qui contient le prédicat `LIKE` sur la colonne **SSN** et une comparaison de plages sur la colonne **Salary**.

1. Remplacez le contenu du fichier Program.cs (généré par Visual Studio) par le code ci-dessous. Mettez à jour la chaîne de connexion de base de données avec le nom de votre serveur et l’URL d’attestation d’enclave pour votre environnement. Vous pouvez aussi mettre à jour les paramètres d’authentification de base de données.

    ```cs
    using System;
    using System.Data.SqlClient;
    using System.Data;

    namespace ConsoleApp1
    {
        class Program
        {
            static void Main(string[] args)
            {
    
                string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = http://hgs.bastion.local/Attestation; Integrated Security = true";

                using (SqlConnection connection = new SqlConnection(connectionString))
                {
                    connection.Open();

                    SqlCommand cmd = connection.CreateCommand();
                    cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";

                    SqlParameter paramSSNPattern = cmd.CreateParameter();

                    paramSSNPattern.ParameterName = @"@SSNPattern";
                    paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
                    paramSSNPattern.Direction = ParameterDirection.Input;
                    paramSSNPattern.Value = "%1111";
                    paramSSNPattern.Size = 11;

                    cmd.Parameters.Add(paramSSNPattern);

                    SqlParameter MinSalary = cmd.CreateParameter();

                    MinSalary.ParameterName = @"@MinSalary";
                    MinSalary.DbType = DbType.Currency;
                    MinSalary.Direction = ParameterDirection.Input;
                    MinSalary.Value = 900;

                    cmd.Parameters.Add(MinSalary);
                    cmd.ExecuteNonQuery();
    
                    SqlDataReader reader = cmd.ExecuteReader();
                    while (reader.Read())

                    {
                        Console.WriteLine(reader);
                        Console.WriteLine(reader[0] + ", " + reader[1] + ", " + reader[2] + ", " + reader[3]);
                    }   
                    Console.ReadKey();
                }
            }
        }
    }
    ```
2. Générez et exécutez l’application.  

## <a name="see-also"></a>Voir aussi
- [Utilisation d’Always Encrypted avec le fournisseur de données .NET Framework pour SQL Server](encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
