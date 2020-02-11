---
title: Définition d’options par programmation pour le pilote dBASE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 27f675cca5115a8336f2be4b7fa96c091aee1b62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063562"
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Définition d’options par programmation pour le pilote dBASE

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nombre approximatif de lignes|Détermine si les statistiques sur la taille de la table sont approximatives. Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.|Pour définir cette option de manière dynamique, utilisez le mot clé **Statistics** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Séquence de classement|Séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être : ASCII (valeur par défaut) ou international.|Pour définir cette option de manière dynamique, utilisez le mot clé **COLLATINGSEQUENCE** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Data Source Name|Nom qui identifie la source de données, telle que la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configurée sans sélectionner ou créer de base de données. Si aucune base de données n’est fournie lors de l’installation, les utilisateurs sont invités à sélectionner un fichier de base de données lorsqu’ils se connectent à la source de données.|Pour définir cette option de manière dynamique, utilisez le mot clé **DBQ** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Description|Description facultative des données dans la source de données ; par exemple, « date d’embauche, historique des salaires et révision actuelle de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **Description** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Exclusif|Si la case **exclusive** est cochée, la base de données est ouverte en mode exclusif et n’est accessible qu’à un seul utilisateur à la fois. Les performances sont améliorées quand elles s’exécutent en mode exclusif.|Pour définir cette option de manière dynamique, utilisez le mot clé **exclusive** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Délai d’attente de la page|Spécifie la durée, en dixièmes de seconde, pendant laquelle une page (si elle n’est pas utilisée) reste dans la mémoire tampon avant d’être supprimée. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’attente de la page ne peut pas être égal à 0 en raison d’un délai inhérent. Le délai d’attente de la page ne peut pas être inférieur au délai inhérent, même si l’option délai d’attente de la page est définie sous cette valeur.|Pour définir cette option de manière dynamique, utilisez le mot clé **PAGETIMEOUT** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le mot clé **ReadOnly** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Sélectionner un répertoire|Affiche une boîte de dialogue dans laquelle vous pouvez sélectionner un répertoire qui contient les fichiers auxquels vous souhaitez accéder.<br /><br /> Lorsque vous définissez un répertoire de source de données, spécifiez le répertoire où se trouvent vos fichiers les plus fréquemment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire s’ils sont utilisés fréquemment. Vous pouvez également qualifier des noms de fichiers dans une instruction SELECT avec le nom de répertoire :<br /><br /> SÉLECTIONNER \* dans C:\MYDIR\EMP<br /><br /> Vous pouvez également spécifier un nouveau répertoire par défaut à l’aide de la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Afficher les lignes supprimées|Spécifie si les lignes qui ont été marquées comme supprimées peuvent être récupérées ou positionnées sur. Si elle est désactivée, les lignes supprimées ne sont pas affichées. Si cette option est sélectionnée, les lignes supprimées sont traitées de la même façon que les lignes non supprimées. Par défaut, cette option est désactivée.|Pour définir cette option de manière dynamique, utilisez le mot clé **Deleted** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
