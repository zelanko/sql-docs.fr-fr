---
title: Résumé de la fonction DLL d’installateur (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddaf20334a84833433961a49e17724d354945c5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298769"
---
# <a name="installer-dll-function-summary"></a>Récapitulatif des fonctions de la DLL d’installation
Le tableau suivant décrit les fonctions dans l’installateur DLL. Pour plus d’informations sur la syntaxe et la sémantique pour chaque fonction, voir [Installer DLL API Référence](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Tâche|Nom de la fonction|Objectif|  
|----------|-------------------|-------------|  
|Installation d’ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Charge la configuration DLL spécifique au conducteur.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Retourne une liste de pilotes installés.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Ajoute un pilote à l’information du système.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Retourne l’annuaire cible pour le Driver Manager.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Renvoie les informations d’erreur ou d’état pour les fonctions d’installateur.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Ajoute un traducteur à l’information du système.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Permet à un pilote ou à une bibliothèque d’installation de traducteurs de signaler les erreurs.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Supprime un conducteur des informations du système.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Supprime les composants de base d’ODBC des informations du système.|  
||[SQLRemoveTranslateur](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Supprime le traducteur des informations du système.|  
|Configuration des sources de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Appelle la configuration spécifique au conducteur DLL.|  
||[SQLCreateDataSource (en anglais)](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Affiche une boîte de dialogue pour ajouter une source de données.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Récupère le mode de configuration qui indique où l’entrée Odbc.ini énumérant les valeurs DSN est dans les informations du système.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Écrit une valeur à l’information du système.|  
||[SQLGetTranslator (SQLGetTranslator)](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Affiche une boîte de dialogue pour sélectionner un traducteur.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Affiche une boîte de dialogue pour configurer les sources de données et les pilotes.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Lit les informations des DNS de fichier.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Supprime la source de données par défaut.|  
||[SQLRemoveDSNDeIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Supprime une source de données.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Définit le mode de configuration qui indique où l’entrée Odbc.ini énumérant les valeurs DSN est dans les informations du système.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Vérifie la durée et la validité du nom de la source de données.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Ajoute une source de données.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Écrit des informations pour déposer des DNS.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Obtient une valeur de l’information du système.|
