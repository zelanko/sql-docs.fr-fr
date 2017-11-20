---
title: "Résumé de la DLL du programme d’installation fonction | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 42b2338cafa53a2813929c3d674d9ed0a9789bdb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="installer-dll-function-summary"></a>Résumé de la fonction DLL programme d’installation
Le tableau suivant décrit les fonctions dans la DLL de programme d’installation. Pour plus d’informations sur la syntaxe et la sémantique pour chaque fonction, consultez [référence d’API de DLL de programme d’installation](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Tâche|Nom de la fonction|Fonction|  
|----------|-------------------|-------------|  
|Installer ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Charge la DLL d’installation spécifiques au pilote.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Retourne une liste des pilotes installés.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Ajoute un pilote aux informations système.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Retourne le répertoire cible pour le Gestionnaire de pilotes.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Retourne des informations d’erreur ou d’état pour les fonctions du programme d’installation.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Ajoute un traducteur d’informations sur le système.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Permet à une bibliothèque le programme d’installation de pilote ou de convertisseur pour signaler des erreurs.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Supprime un pilote à partir des informations système.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Supprime des composants ODBC à partir des informations système.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Supprime la traduction à partir des informations système.|  
|Configuration des sources de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Appelle la DLL d’installation spécifiques au pilote.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Affiche une boîte de dialogue pour ajouter une source de données.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Récupère le mode de configuration qui indique l’entrée du fichier Odbc.ini répertoriant les valeurs de la source de données dans les informations système.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Écrit une valeur dans les informations système.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Affiche une boîte de dialogue pour sélectionner un convertisseur.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Affiche une boîte de dialogue pour configurer les pilotes et les sources de données.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Lit les informations à partir du fichier DSN.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Supprime la source de données par défaut.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Supprime une source de données.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Définit le mode de configuration qui indique l’entrée du fichier Odbc.ini répertoriant les valeurs de la source de données dans les informations système.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Vérifie la longueur et la validité du nom de la source de données.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Ajoute une source de données.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Écrit les informations dans le fichier DSN.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Obtient une valeur à partir des informations système.|

