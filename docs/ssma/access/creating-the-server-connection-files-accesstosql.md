---
title: "Créez les fichiers de connexion du serveur (AccessToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 7812e5ad1b6566a3ef477800d8098b23abacdd6a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="creating-the-server-connection-files-accesstosql"></a>Création du serveur de fichiers de connexion (AccessToSQL)
Informations sur le serveur peuvent être spécifié dans la section serveurs du fichier de script. Informations sur le serveur peuvent également être spécifiées dans un fichier de connexion de serveur distinct. Le paramètre de ligne de commande pour le fichier de connexion de serveur est `-c <serverconnectionfile>`. Si le même id de serveur est présent dans le script et le serveur de fichiers de connexion, la définition de serveur dans le fichier de script est pris en compte.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Validation de fichier de connexion de serveur  
L’utilisateur peut valider facilement son fichier de connexion de serveur par rapport au fichier de définition de schéma **'A2SSConsoleScriptServersSchema.xsd'** disponibles dans le dossier « Schémas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante d’exploitation de la console est [l’exécution de la Console SSMA &#40; AccessToSQL &#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[L’exécution de la Console SSMA (accès)](http://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  

