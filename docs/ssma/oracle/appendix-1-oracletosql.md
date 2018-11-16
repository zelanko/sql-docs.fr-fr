---
title: Annexe - 1 (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2539ac90fcce2dd1d5b30384c07bac620d809f0a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668238"
---
# <a name="appendix---1-oracletosql"></a>Annexe - 1 (OracleToSQL)
Aperçu rapide des options de ligne de commande de la Console SSMA :  
  
|Sl. Non.|Commutateur|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s ou des scripts|Oui|scriptfile|Nom du fichier XML valide.<br /><br />Fichier de définition du Script de console.|  
|2|-v/variable|non|variablevaluefile|Nom du fichier XML valide.<br /><br />Si les variables sont utilisées dans le fichier de script, ce fichier doit être spécifié.|  
|3|-c/serverconnection|non|serverconnectionfile|Nom du fichier XML valide.<br /><br />Ce fichier contient des informations de connexion de serveur.|  
|4|-x/xmloutput|non|xmloutputfile|Cette option indique la sortie de console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée vers `STDOUT`.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de console est écrite au format XML.|  
|5|-l/log|non|logfile|Nom de fichier valide.|  
|6|-e/projectenvironment|non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/securepassword|non|-a/Ajouter {< server_id > [,... n] &#124; tous les} – c&#124;serverconnection < fichier de connexion serveur > [-v&#124;variable < variable-valeur-file >] [-remplacer/o]<br /><br />ou Gestionnaire de configuration<br /><br />-a/Ajouter {< server_id > [,... n] &#124; tous les} – s&#124;script < fichier de script-> [-v&#124;variable < variable-valeur-file >] [-remplacer/o]<br /><br />– r/supprimer {< server_id > [,... n] &#124; tous les}<br /><br />-l/liste<br /><br />– e/export {< server-id > [,... n] &#124; tous les} < chiffré-password - fichier ><br /><br />– i / importation {< server-id > [,... n] &#124; tous les} < chiffré-mot de passe-file >|Si spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />id de serveur : un ID unique fourni pour un serveur {string}<br /><br />fichier de connexion de serveur : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />fichier de valeurs de variable : il est un fichier de définition de variable et utilisé dans le fichier de connexion de serveur.<br /><br />fichier de mot de passe chiffré : c’est un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifié par l’utilisateur.|  
|8|-?|non|Non Applicable|Non Applicable|  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la Console SSMA (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
