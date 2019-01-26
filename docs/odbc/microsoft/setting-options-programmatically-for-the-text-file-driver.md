---
title: Définition des Options par programmation pour le pilote de fichier texte | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04bd9a37d87c91fe3f42cbb1fdf464660ba5a299
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044416"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Définition d’options par programmation pour le pilote de fichier texte

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nom de la source de données|Un nom qui identifie la source de données, telles que la paie ou Personnel.|Pour définir cette option de manière dynamique, utilisez le **DSN** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Définir le Format|Affiche le **définition du Format texte** boîte de dialogue et vous permet de spécifier le schéma pour des tables individuelles dans le répertoire de source de données.|Cette option ne peut pas définir de manière dynamique par un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Description|Une description facultative des données dans la source de données ; par exemple, « date d’embauche, historique de salaire et examen actuel de tous les employés. »|Pour définir cette option de manière dynamique, utilisez le **DESCRIPTION** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Répertoire|Sélectionne le répertoire cible.|Pour définir cette option de manière dynamique, utilisez le **DEFAULTDIR** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Liste des extensions|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données. Lorsque le pilote de texte est utilisé, un fichier sans extension est créé lorsque l’instruction CREATE TABLE est exécutée avec un nom qui n’a aucune extension. Autres pilotes de créer un fichier avec une extension par défaut lorsque aucune extension ne soit fournie. Pour créer un fichier avec une extension .txt, l’extension doit être incluse dans le nom. Pour afficher les fichiers sans extensions dans le **définition du Format texte** boîte de dialogue, « *. » doit être ajouté à la liste des Extensions.|Pour définir cette option de manière dynamique, utilisez le **EXTENSIONS** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le **READONLY** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Lignes à balayer|Le nombre de lignes à analyser pour déterminer le type de données de chaque colonne. Le type de données est déterminé étant donné le nombre maximal de types de données trouvées. Si les données qui ne correspond pas au type de données estimé pour la colonne sont rencontrées, le type de données sera retourné comme une valeur NULL.<br /><br /> Pour le pilote de texte, vous pouvez entrer un nombre compris entre 1 et 32 767 pour le nombre de lignes à analyser ; Toutefois, la valeur toujours par défaut 25. (Un nombre en dehors de la limite retournera une erreur).|Pour définir cette option de manière dynamique, utilisez le **MAXSCANROWS** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Sélectionnez le répertoire|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire contenant les fichiers que vous souhaitez accéder.<br /><br /> Lorsque la définition d’un répertoire de source de données spécifiez le répertoire où le plus couramment utilisés fichiers se trouvent. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire si elles sont utilisées fréquemment. Ou bien, vous pouvez qualifier les noms de fichiers dans une instruction SELECT avec le nom du répertoire : `SELECT * FROM C:\MYDIR\EMP`<br /><br /> Ou, vous pouvez spécifier un répertoire par défaut à l’aide de la **SQLSetConnectOption** fonction avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le **DEFAULTDIR** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
