---
title: Annexe - 1 (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 00665e16-2990-4bfc-8e17-d97ca9fb4999
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d750afec53670a06b6e10cd654c114502e088169
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47630307"
---
# <a name="appendix---1-accesstosql"></a>Annexe - 1 (AccessToSQL)
Aperçu rapide des options de ligne de commande de la Console SSMA :  
  
|Sl. Non.|Commutateur|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s ou des scripts|Oui|scriptfile|Nom du fichier XML valide.<br /><br />Fichier de définition du Script de console.|  
|2|-v/variable|non|variablevaluefile|Nom du fichier XML valide. Si les variables sont utilisées dans le fichier de script, ce fichier doit être spécifié.|  
|3|-c/serverconnection|non|serverconnectionfile|Nom du fichier XML valide. Ce fichier contient des informations de connexion de serveur.|  
|4|-x/xmloutput|non|xmloutputfile|Cette option indique la sortie de console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée dans STDOUT.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de console est écrite au format XML.|  
|5|-l/log|non|logfile|Nom de fichier valide.|  
|6|-e/projectenvironment|non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/securepassword|non|-a/Ajouter {< server_id > [,... n] &#124; tous les} – c&#124;serverconnection < fichier de connexion serveur > [-v&#124;variable < variable-valeur-file >] [-remplacer/o]<br /><br />ou Gestionnaire de configuration<br /><br />-a/Ajouter {< server_id > [,... n] &#124; tous les} – s&#124;script < fichier de script-> [-v&#124;variable < variable-valeur-file >] [-remplacer/o]<br /><br />– r/supprimer {< server_id > [,... n] &#124; tous les}<br /><br />-l/liste<br /><br />– e/export {< server-id > [,... n] &#124; tous les} < chiffré-password - fichier ><br /><br />– i / importation {< server-id > [,... n] &#124; tous les} < chiffré-mot de passe-file >|Si spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />id de serveur : un ID unique fourni pour un serveur {string}<br /><br />fichier de connexion de serveur : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />fichier de valeurs de variable : il est un fichier de définition de variable et utilisé dans le fichier de connexion de serveur.<br /><br />mot de passe – fichier chiffré : c’est un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifié par l’utilisateur.|  
|8|-?|non|Non Applicable|Non Applicable|  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la Console SSMA (accès)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
