---
title: Annexe - 1 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c6a30367-d56f-4fcc-8920-c6a6b0335a67
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 70d916526f5b7d7d36c9237624ef311befca39c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938357"
---
# <a name="appendix---1-db2tosql"></a>Annexe - 1 (DB2ToSQL)
Aperçu rapide des options de ligne de commande de la Console SSMA :  
  
|Sl. Non.|Basculer|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Oui|scriptfile|Nom du fichier XML valide.<br /><br />Fichier de définition du Script de console.|  
|2|-v/variable|Non|variablevaluefile|Nom du fichier XML valide.<br /><br />Si les variables sont utilisées dans le fichier de script, ce fichier doit être spécifié.|  
|3|-c/serverconnection|Non|serverconnectionfile|Nom du fichier XML valide.<br /><br />Ce fichier contient des informations de connexion de serveur.|  
|4|-x/xmloutput|Non|xmloutputfile|Cette option indique la sortie de console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée dans STDOUT.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de console est écrite au format XML.|  
|5\.|-l/log|Non|logfile|Nom de fichier valide.|  
|6\.|-e/projectenvironment|Non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/securepassword|Non|-a/Ajouter {< server_id > [,... n] &#124; tous les} - c&#124;serverconnection < fichier de connexion serveur > [-v&#124;variable < variable-valeur-file >] [-remplacer/o]<br /><br />ou Gestionnaire de configuration<br /><br />-a/Ajouter {< server_id > [,... n] &#124; tous les} -s&#124;script < fichier de script-> [-v&#124;variable < variable-valeur-file >] [-remplacer/o]<br /><br />-r/remove {< server_id > [,... n] &#124; tous les}<br /><br />-l/liste<br /><br />-e/export {< server-id > [,... n] &#124; tous les} < chiffré-password - fichier ><br /><br />-i / importation {< server-id > [,... n] &#124; tous les} < chiffré-mot de passe-file >|Si spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />id de serveur : Un ID unique fourni pour un serveur {string}<br /><br />fichier de connexion de serveur : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />variable-valeur-file : Il est un fichier de définition de variable et utilisé dans le fichier de connexion de serveur.<br /><br />mot de passe-fichier chiffré : C’est un fichier de mots de passe serveur chiffré à l’aide d’une phrase secrète spécifié par l’utilisateur.|  
|8|-?|Non|Non Applicable|Non Applicable|  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
