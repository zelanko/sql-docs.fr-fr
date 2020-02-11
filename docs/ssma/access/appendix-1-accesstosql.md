---
title: Annexe-1 (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 00665e16-2990-4bfc-8e17-d97ca9fb4999
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: ca084ec1849ab22940bb1617476637c105e90609
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68115029"
---
# <a name="appendix---1-accesstosql"></a>Annexe-1 (AccessToSQL)
Affichage rapide des options de ligne de commande de la console SSMA :  
  
|SL. Non.|Commutateur|Obligatoire ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Oui|scriptfile|Nom de fichier XML valide.<br /><br />Fichier de définition de script de console.|  
|2|-v/variable|Non|variablevaluefile|Nom de fichier XML valide. Si des variables sont utilisées dans un fichier de script, ce fichier doit être spécifié.|  
|3|-c/ServerConnection|Non|serverconnectionfile|Nom de fichier XML valide. Ce fichier contient des informations de connexion au serveur.|  
|4|-x/XMLOutput|Non|xmloutputfile|Cette option indique la sortie de la console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée vers STDOUT.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de la console est écrite au format XML.|  
|5|-l/log|Non|logfile|Nom de fichier valide.|  
|6|-e/projectenvironment|Non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/SecurePassword|Non|-a/Add {<server_id> [,... n] &#124; All}-c&#124;ServerConnection <Server-Connection-File> [-v&#124;variable <variable-value-file>] [-o/Overwrite]<br /><br />or<br /><br />-a/Add {<server_id> [,... n] &#124; tous les fichiers de script}-s&#124;<> de fichier de script [-v&#124;variable <variable-valeur-fichier>] [-o/Overwrite]<br /><br />-r/supprimer {<server_id> [,... n] &#124; tout}<br /><br />-l/liste<br /><br />-e/export {<Server-ID> [,... n] &#124; tous} <fichier de mot de passe chiffré><br /><br />-i/import {<Server-ID> [,... n] &#124; tous} <fichier de mot de passe chiffré>|S’il est spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />Server-ID : ID unique fourni pour un serveur {String}<br /><br />Server-Connection-file : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />variable-value-file : il s’agit d’un fichier de définition de variable et il est utilisé dans le fichier de connexion de serveur.<br /><br />encrypted-password-file : il s’agit d’un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifiée par l’utilisateur.|  
|8|-?|Non|Non applicable|Non applicable|  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA (accès)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
