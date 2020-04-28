---
title: Définition d’options par programmation pour le pilote de fichier texte | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e19c3b49479047bc92a7b6f72359d4951d8df16e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300749"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Définition d’options par programmation pour le pilote de fichier texte

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nom de la source de données|Nom qui identifie la source de données, telle que la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Définir le format|Affiche la boîte de dialogue **définir le format du texte** et vous permet de spécifier le schéma des tables individuelles dans le répertoire de la source de données.|Cette option ne peut pas être définie dynamiquement par un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Description|Description facultative des données dans la source de données ; par exemple, « date d’embauche, historique des salaires et révision actuelle de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **Description** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Répertoire|Sélectionne le répertoire ciblé.|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Liste des extensions|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données. Lorsque le pilote de texte est utilisé, un fichier sans extension est créé lorsque l’instruction CREATE TABLE est exécutée avec un nom qui n’a pas d’extension. D’autres pilotes créent un fichier avec une extension par défaut quand aucune extension n’est fournie. Pour créer un fichier avec une extension. txt, l’extension doit être incluse dans le nom. Pour afficher les fichiers sans extensions dans la boîte de dialogue **définir le format de texte** , « *. » doit être ajouté à la liste des extensions.|Pour définir cette option de manière dynamique, utilisez le mot clé **Extensions** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le mot clé **ReadOnly** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Lignes à analyser|Nombre de lignes à analyser pour déterminer le type de données de chaque colonne. Le type de données est déterminé en fonction du nombre maximal de types de données trouvés. Si des données qui ne correspondent pas au type de données devinées pour la colonne sont rencontrées, le type de données est retourné en tant que valeur NULL.<br /><br /> Pour le pilote Text, vous pouvez entrer un nombre compris entre 1 et 32767 pour le nombre de lignes à analyser. Toutefois, la valeur par défaut sera toujours 25. (Un nombre en dehors de la limite renverra une erreur.)|Pour définir cette option de manière dynamique, utilisez le mot clé **MaxScanRows** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Sélectionner un répertoire|Affiche une boîte de dialogue dans laquelle vous pouvez sélectionner un répertoire contenant les fichiers auxquels vous souhaitez accéder.<br /><br /> Lors de la définition d’un répertoire de source de données, spécifiez le répertoire dans lequel se trouvent les fichiers les plus couramment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire s’ils sont utilisés fréquemment. Vous pouvez également qualifier des noms de fichiers dans une instruction SELECT avec le nom de répertoire :`SELECT * FROM C:\MYDIR\EMP`<br /><br /> Vous pouvez également spécifier un nouveau répertoire par défaut à l’aide de la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
