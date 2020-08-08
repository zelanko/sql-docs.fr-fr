---
title: Annexe-1 (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 17bc5783d70b4b2f7667b7c9cbf5cdf7d9fae030
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935008"
---
# <a name="appendix---1-oracletosql"></a>Annexe - 1 (OracleToSQL)
Affichage rapide des options de ligne de commande de la console SSMA :  
  
|SL. Non.|Basculer|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Yes|scriptfile|Nom de fichier XML valide.<br /><br />Fichier de définition de script de console.|  
|2|-v/variable|No|variablevaluefile|Nom de fichier XML valide.<br /><br />Si des variables sont utilisées dans un fichier de script, ce fichier doit être spécifié.|  
|3|-c/ServerConnection|No|serverconnectionfile|Nom de fichier XML valide.<br /><br />Ce fichier contient des informations de connexion au serveur.|  
|4|-x/XMLOutput|No|xmloutputfile|Cette option indique la sortie de la console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée vers `STDOUT` .<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de la console est écrite au format XML.|  
|5|-l/log|No|logfile|Nom de fichier valide.|  
|6|-e/projectenvironment|No|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/SecurePassword|No|-a/Add {<server_id> [,... n] &#124; All}-c&#124;ServerConnection <Server-Connection-File> [-v&#124;variable <variable-value-file>] [-o/Overwrite]<br /><br />ou<br /><br />-a/Add {<server_id> [,... n] &#124; tous les fichiers de script}-s&#124;<> de fichier de script [-v&#124;variable <variable-valeur-fichier>] [-o/Overwrite]<br /><br />-r/supprimer {<server_id> [,... n] &#124; tout}<br /><br />-l/liste<br /><br />-e/export {<Server-ID> [,... n] &#124; tous} <fichier de mot de passe chiffré><br /><br />-i/import {<Server-ID> [,... n] &#124; tous} <fichier de mot de passe chiffré>|S’il est spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />Server-ID : ID unique fourni pour un serveur {String}<br /><br />Server-Connection-file : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />variable-value-file : il s’agit d’un fichier de définition de variable et il est utilisé dans le fichier de connexion de serveur.<br /><br />encrypted-password-file : il s’agit d’un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifiée par l’utilisateur.|  
|8|-?|No|Non applicable|Non applicable|  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
