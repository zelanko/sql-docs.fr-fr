---
title: La gestion des mots de passe (DB2ToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 56d546e3-8747-4169-aace-693302667e94
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e6ee12eb7a0d75c503906046e05cef4d61180d7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="managing-passwords-db2tosql"></a>La gestion des mots de passe (DB2ToSQL)
Cette section est sur la sécurisation de la procédure pour importer ou exporter les sur les serveurs et les mots de passe de base de données :  
  
1.  Sécurisation de mot de passe  
  
2.  Exportation et importation de mot de passe chiffré  
  
## <a name="securing-password"></a>Sécurisation de mot de passe  
SSMA vous permet de sécuriser votre mot de passe d’une base de données.  
  
Pour implémenter une connexion sécurisée, utilisez la procédure suivante :  
  
Spécifiez un mot de passe à l’aide d’une des trois méthodes suivantes :  
  
1.  **Texte clair :** tapez le mot de passe de base de données dans l’attribut de la valeur du nœud « password ». Il se trouve sous le nœud de définition de serveur dans la section serveur du fichier de script ou du fichier de connexion de serveur.  
  
    Les mots de passe en texte clair ne sont pas sécurisées. Par conséquent, vous rencontrerez le message d’avertissement suivant dans la sortie de console : *» serveur &lt;id de serveur&gt; mot de passe est fournie sous forme de texte en clair non sécurisées, application Console SSMA fournit une option pour protéger le mot de passe via le chiffrement, consultez l’option – securepassword dans le fichier d’aide SSMA pour plus d’informations. »*  
  
    **Mots de passe chiffrés :** le mot de passe, dans ce cas, est stocké dans un formulaire chiffré sur l’ordinateur local dans ProtectedStorage.ssma.  
  
    -   **Sécurisation des mots de passe**  
  
        -   Exécutez le `SSMAforDB2Console.exe` avec le `–securepassword` et ajoutez le commutateur à la ligne de commande en passant le serveur de connexion ou fichier de script contenant le nœud de mot de passe dans la section de définition de serveur.  
  
        -   À l’invite de commandes, l’utilisateur est invité à entrer le mot de passe et confirmez-le.  
  
            Les ID de définition de serveur et de ses mots de passe chiffrés correspondants sont stockés dans un fichier sur l’ordinateur local  
            
            Exemple 1 :
            
                Specify password
                C:\SSMA\SSMAforDB2Console.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Exemple 2 :
            
                C:\SSMA\SSMAforDB2Console.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Suppression des mots de passe chiffrés**  
  
        Exécutez le `SSMAforDB2Console.exe` avec la`–securepassword` et `–remove` passer à la ligne de commande en passant l’ID de serveur pour supprimer les mots de passe chiffrés à partir du fichier de stockage protégé présent sur l’ordinateur local.  
  
        Exemple :  
        
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –remove all
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Liste des ID de serveur dont les mots de passe sont chiffrés.**  
  
        Exécutez le `SSMAforDB2Console.exe` avec la `–securepassword` et `–list` passer à la ligne de commande pour répertorier tous les ID de serveur dont les mots de passe ont été chiffrés.  
  
        Exemple :  
        
            C:\SSMA\SSMAforDB2Console.EXE –securepassword –list  

  
    > [!NOTE]  
    > 1.  Le mot de passe en texte clair mentionné dans le fichier de connexion de serveur ou de script est prioritaire sur le mot de passe chiffré dans le fichier sécurisé.  
    > 2.  Lorsqu’aucun mot de passe existe déjà dans la section serveur de fichier de connexion de serveur ou le fichier de script, ou si elle n’a pas été sécurisée sur l’ordinateur local, la console vous invite à entrer le mot de passe.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Exporter ou importer des mots de passe chiffrés  
L’application Console de SSMA vous permet d’exporter les mots de passe chiffré de la base de données présents dans un fichier sur l’ordinateur local à un fichier sécurisé et inversement. Il est utile dans la création de l’ordinateur de mots de passe chiffrés indépendant. Fonctionnalité d’exportation lit l’id du serveur et le mot de passe de l’ordinateur local, stockage protégé et enregistre les informations dans un fichier chiffré. L’utilisateur est invité à entrer le mot de passe pour le fichier sécurisé. Assurez-vous que le mot de passe est 8 caractères ou plus. Ce fichier sécurisé peut être utilisé sur des ordinateurs différents. Fonctionnalité d’importation lit le serveur id et mot de passe à partir du fichier sécurisé. L’utilisateur est invité à entrer le mot de passe pour le fichier sécurisé et ajoute les informations dans le stockage protégé local.  
  
Exemple :  

    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforDB2Console.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforDB2Console.EXE –p –e "DB2DB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Exemple :  

    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforDB2Console.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforDB2Console.EXE –p –i "DB2DB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx

  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA](http://msdn.microsoft.com/en-us/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
