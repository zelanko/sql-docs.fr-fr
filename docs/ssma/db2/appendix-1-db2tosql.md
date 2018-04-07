---
title: Appendix - 1 (DB2ToSQL) | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c6a30367-d56f-4fcc-8920-c6a6b0335a67
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e06f1f7e7152bb65f6c6625c87ad3fdb7542ac7
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="appendix---1-db2tosql"></a>Appendix - 1 (DB2ToSQL)
Aperçu rapide des options de ligne de commande de Console de SSMA :  
  
|Sl. Non.|Commutateur|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Oui|scriptfile|Nom de fichier XML valide.<br /><br />Fichier de Script de définition de la console.|  
|2|variable ou - v|non|variablevaluefile|Nom de fichier XML valide.<br /><br />Si les variables sont utilisées dans le fichier de script, ce fichier doit être spécifié.|  
|3|-c/serverconnection|non|serverconnectionfile|Nom de fichier XML valide.<br /><br />Ce fichier contient des informations de connexion de serveur.|  
|4|-x/xmloutput|non|xmloutputfile|Cette option indique la sortie de la console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée dans STDOUT.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de console est écrite au format XML.|  
|5|-l/journal|non|logfile|Nom de fichier valide.|  
|6|-e/projectenvironment|non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/securepassword|non|-une/add {< server_id > [,... n] &#124; tous les} – c&#124;serverconnection < fichier de connexion serveur > [-v&#124;variable < variable-valeur-fichier >] [-o/remplacer]<br /><br />ou<br /><br />-a/add {<server_id> [,…n] &#124; all} –s&#124;script <script-file> [-v&#124;variable <variable-value-file>] [-o/overwrite]<br /><br />–r/remove {<server_id> [, …n] &#124; all}<br /><br />-l/liste<br /><br />– e/exportation {< server-id > [,... n] &#124; tous les} < chiffré-password - fichier ><br /><br />–i/import {<server-id> [, …n] &#124; all} <encrypted-password-file>|Si spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />id du serveur : un ID unique est fournie pour un serveur {string}<br /><br />fichier de connexion de serveur : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />fichier de valeurs de variable : il est un fichier de définition de la variable et utilisé dans le fichier de connexion de serveur.<br /><br />mot de passe chiffré – fichier : il est un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifiée par l’utilisateur.|  
|8|-?|non|Non Applicable|Non Applicable|  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA](http://msdn.microsoft.com/en-us/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
