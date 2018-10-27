---
title: Création des fichiers de connexion de serveur (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Server connection file validation
- Server connection files
ms.assetid: df0e970c-da0b-4118-b359-c9dcbbad16d6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6cd954964af9c2495311423620c95af621021a5b
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50099241"
---
# <a name="creating-the-server-connection-files-mysqltosql"></a>Création des fichiers de connexion de serveur (MySQLToSQL)
Informations sur le serveur peuvent être spécifiées dans la section serveurs du fichier de script ou dans un fichier de connexion de serveur distinct. Le paramètre de ligne de commande pour le fichier de connexion de serveur est, `-c <serverconnectionfile>`. Si le même id de serveur est présent dans le fichier de script et le fichier de connexion de serveur, la définition du serveur dans le fichier de script est considéré comme.  
  
**Exemple :**  
  
```xml  
<!--Sample of server connection file commands -->  
  
<mysql name ="<source-server-unique-name>">  
  
   <standard-mode>  
  
      <server value ="<server-name>"/>  
  
      <user-id value ="<user-name>"/>  
  
      <password value ="<password>"/>  
  
      <port value ="<port>"/>  
  
   </standard-mode>  
  
</mysql>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
   <sql-server-authentication>  
  
      <server value="<server-name>"/>  
  
      <database value="<database-name>"/>  
  
      <user-id value="<user-name>"/>  
  
      <password value="<password>"/>  
  
      <encrypt value="<true/false>"/>  
  
      <trust-server-certificate value="<true/false>"/>  
  
   </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="<target-server-unique-name>">  
  
   <server value="<server-name>"/>  
  
   <database value="<database-name>"/>  
  
   <user-id value="<user-name>"/>  
  
   <password value="<password>"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Validation de fichier de connexion de serveur  
L’utilisateur peut valider facilement son fichier de connexion de serveur par rapport au fichier de définition de schéma **'M2SSConsoleScriptServersSchema.xsd'** disponibles dans le dossier « Schémas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de d’exploitation de la console est [l’exécution de la Console SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la Console SSMA (MySQL)](http://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
