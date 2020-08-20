---
description: Définition d’options par programmation pour le pilote Paradox
title: Définition d’options par programmation pour le pilote Paradox | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 85b63df9e18b835c96bc0e59f7c937ece69f3999
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471571"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Définition d’options par programmation pour le pilote Paradox

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Répertoire|Définit le répertoire ciblé.|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Séquence de classement|Séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être ASCII (valeur par défaut), international, suédois-finnois ou norvégien-danois.|Pour définir cette option de manière dynamique, utilisez le mot clé **COLLATINGSEQUENCE** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Description|Description facultative des données dans la source de données ; par exemple, « date d’embauche, historique des salaires et révision actuelle de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **Description** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exclusif|Si la case **exclusive** est cochée, la base de données est ouverte en mode exclusif et n’est accessible qu’à un seul utilisateur à la fois. Les performances sont améliorées lors de l’exécution en mode exclusif.|Pour définir cette option de manière dynamique, utilisez le mot clé **exclusive** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Style net|Style d’accès réseau à utiliser lors de l’accès aux données Paradox : « 3.*x*» pour Paradox 3. *x* ou «4. *x*"pour Paradox 4. *x* ou 5. *x*. Peut avoir la valeur « 3 ». *x*"ou" 4. *x*» si la version est Paradox 4. *x* ou 5. *x*; Si la version est Paradox 3. *x*, le style doit être «3. *x*».|Pour définir cette option de manière dynamique, utilisez le mot clé **PARADOXNETSTYLE** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Délai d’attente de la page|Spécifie la durée, en dixièmes de seconde, pendant laquelle une page (si elle n’est pas utilisée) reste dans la mémoire tampon avant d’être supprimée. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’attente de la page ne peut pas être égal à 0 en raison d’un délai inhérent. Le délai d’attente de la page ne peut pas être inférieur au délai inhérent, même si l’option délai d’attente de la page est définie sous cette valeur.|Pour définir cette option de manière dynamique, utilisez le mot clé **PAGETIMEOUT** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le mot clé **ReadOnly** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sélectionner un répertoire|Affiche une boîte de dialogue dans laquelle vous pouvez sélectionner un répertoire contenant les fichiers auxquels vous souhaitez accéder.<br /><br /> Lors de la définition d’un répertoire de source de données, spécifiez le répertoire dans lequel se trouvent les fichiers les plus couramment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire s’ils sont utilisés fréquemment. Vous pouvez également qualifier des noms de fichiers dans une instruction SELECT avec le nom de répertoire :<br /><br /> SÉLECTIONNER \* dans C:\MYDIR\EMP<br /><br /> Vous pouvez également spécifier un nouveau répertoire par défaut à l’aide de la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sélectionner un répertoire réseau|Chemin d’accès complet du répertoire contenant une base de données de verrouillage Paradox, car il contient le fichier Pdoxusrs.net (dans Paradox 4.* x*) ou le fichier Paradox.net (dans Paradox 5.* x*). Si le répertoire ne contient pas l’un de ces fichiers, le pilote Paradox en crée un. Pour plus d’informations sur ces fichiers, consultez la documentation relative à Paradox.<br /><br /> Avant de pouvoir sélectionner un répertoire réseau, vous devez entrer votre nom d’utilisateur Paradox dans la zone de texte **nom d’utilisateur** . Cliquez sur **Sélectionner un répertoire réseau** pour sélectionner un répertoire réseau.|Pour définir cette option de manière dynamique, utilisez le mot clé **PARADOXNETPATH** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|User Name|Nom d’utilisateur Paradox. Il s’agit du nom affiché par d’autres utilisateurs des fichiers Paradox lorsqu’un verrou est rencontré.|Pour définir cette option de manière dynamique, utilisez le mot clé **PARADOXUSERNAME** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
