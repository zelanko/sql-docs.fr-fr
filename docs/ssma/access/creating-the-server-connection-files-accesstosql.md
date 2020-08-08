---
title: Création des fichiers de connexion au serveur (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: b74cf86e6a68653a2047aebefc7ca86ab6868475
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933980"
---
# <a name="creating-the-server-connection-files-accesstosql"></a>Création des fichiers de connexion au serveur (AccessToSQL)
Les informations sur le serveur peuvent être spécifiées dans la section serveurs du fichier de script. Les informations du serveur peuvent également être spécifiées dans un fichier de connexion au serveur distinct. Le paramètre de ligne de commande du fichier de connexion au serveur est `-c <serverconnectionfile>` . Si le même ID de serveur est présent dans les fichiers de script et de connexion au serveur, la définition de serveur dans le fichier de script est alors prise en compte.  
  
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
  
## <a name="server-connection-file-validation"></a>Validation du fichier de connexion au serveur  
L’utilisateur peut facilement valider son fichier de connexion au serveur par rapport au fichier de définition de schéma **« A2SSConsoleScriptServersSchema. xsd »** disponible dans le dossier « schemas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de l’utilisation de la console est l' [exécution de la console SSMA &#40;AccessToSQL&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA (accès)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
