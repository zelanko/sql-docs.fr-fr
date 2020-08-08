---
title: Création des fichiers de connexion au serveur (MySQLToSQL) | Microsoft Docs
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: fa9505c0f5c40dcf2ff7cd84fc956240728385b3
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935728"
---
# <a name="creating-the-server-connection-files-mysqltosql"></a>Création des fichiers de connexion de serveur (MySQLToSQL)
Les informations sur le serveur peuvent être spécifiées dans la section serveurs du fichier de script ou dans un fichier de connexion au serveur distinct. Le paramètre de ligne de commande du fichier de connexion au serveur est, `-c <serverconnectionfile>` . Si le même ID de serveur est présent dans le fichier de script et le fichier de connexion au serveur, la définition du serveur dans le fichier de script est prise en compte.  
  
**Exemple :**  
  
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
  
## <a name="server-connection-file-validation"></a>Validation du fichier de connexion au serveur  
L’utilisateur peut facilement valider son fichier de connexion de serveur par rapport au fichier de définition de schéma « **2ssconsolescriptserversschema. xsd »** disponible dans le dossier « schemas ».  
  
## <a name="next-step"></a>étape suivante  
L’étape suivante de l’utilisation de la console est l' [exécution de la console SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA (MySQL)](https://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
