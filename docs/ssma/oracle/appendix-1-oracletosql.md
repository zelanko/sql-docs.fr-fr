---
title: Annexe - 1 (OracleToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1dc360647251f526764ebb0d86fd0b7931aa7e9d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="appendix---1-oracletosql"></a>Annexe - 1 (OracleToSQL)
Aperçu rapide des options de ligne de commande de Console de SSMA :  
  
|Sl. Non.|Commutateur|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Oui|scriptfile|Nom de fichier XML valide.<br /><br />Fichier de Script de définition de la console.|  
|2|variable ou - v|Non|variablevaluefile|Nom de fichier XML valide.<br /><br />Si les variables sont utilisées dans le fichier de script, ce fichier doit être spécifié.|  
|3|-c/serverconnection|Non|serverconnectionfile|Nom de fichier XML valide.<br /><br />Ce fichier contient des informations de connexion de serveur.|  
|4|x-/ xmloutput|Non|xmloutputfile|Cette option indique la sortie de la console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée vers `STDOUT`.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de console est écrite au format XML.|  
|5|-l/journal|Non|logfile|Nom de fichier valide.|  
|6|e/projectenvironment|Non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/securepassword|Non|-une/add {< server_id > [,... n] &#124; toutes les} – c &#124; serverconnection < fichier de connexion serveur > [-v &#124; variable < variable-valeur-fichier >] [-o/remplacer]<br /><br />ou<br /><br />-une/add {< server_id > [,... n] &#124; toutes les} – s &#124; le script < fichier de script > [-v &#124; variable < variable-valeur-fichier >] [-o/remplacer]<br /><br />– r/supprimer {< server_id > [,... n] &#124; toutes les}<br /><br />-l/liste<br /><br />– e/exportation {< server-id > [,... n] &#124; toutes les} < chiffré-password - fichier ><br /><br />– i / importation {< server-id > [,... n] &#124; toutes les} < chiffré-mot de passe-fichier >|Si spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />id du serveur : un ID unique est fournie pour un serveur {string}<br /><br />fichier de connexion de serveur : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />fichier de valeurs de variable : il est un fichier de définition de la variable et utilisé dans le fichier de connexion de serveur.<br /><br />fichier de mot de passe chiffré : c’est un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifiée par l’utilisateur.|  
|8|-?|Non|Non Applicable|Non Applicable|  
  
## <a name="see-also"></a>Voir aussi  
[L’exécution de la Console SSMA (Oracle)](http://msdn.microsoft.com/en-us/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  

