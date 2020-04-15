---
title: Définir des options programmatiquement pour le pilote Paradox (fr) Microsoft Docs
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
ms.openlocfilehash: d04de1f0de4baca5b3f474ef9fbcf3f886e6906f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300759"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Définition d’options par programmation pour le pilote Paradox

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Répertoire|Définit le répertoire ciblé.|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Séquence de collation|La séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être ASCII (par défaut), Internationale, suédoise-finlandaise ou norvégienne-danoise.|Pour définir cette option de manière dynamique, utilisez le mot clé **COLLATINGSEQUENCE** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Description|Une description facultative des données dans la source de données; par exemple, « La date de location, les antécédents salariaux et l’examen actuel de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **DESCRIPTION** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exclusif|Si la boîte **exclusive** est sélectionnée, la base de données sera ouverte en mode Exclusif et peut être consultée par un seul utilisateur à la fois. Les performances sont améliorées lors de l’exécution en mode exclusif.|Pour définir cette option dynamiquement, utilisez le mot clé **EXCLUSIF** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Net Style|Le style d’accès réseau à utiliser lors de l’accès aux données Paradox: soit "3.*x"* pour Paradox 3. *x* ou "4. *x*" pour Paradox 4. *x* ou 5. *x*. Peut être réglé à "3. *x*" ou " 4. *x*" si la version est Paradox 4. *x* ou 5. *x*; si la version est Paradox 3. *x*, le style doit être "3. *x*".|Pour définir cette option de manière dynamique, utilisez le mot clé **PARADOXNETSTYLE** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Délai d’attente de page|Spécifie la période de temps, en dixièmes de seconde, qu’une page (si elle n’est pas utilisée) reste dans le tampon avant d’être supprimée. La valeur par défaut est de 600 dixièmes de seconde (60 secondes). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’attente de page ne peut pas être 0 en raison d’un retard inhérent. Le délai d’attente de page ne peut pas être inférieur au délai inhérent, même si l’option de délai d’arrêt de page est définie en dessous de cette valeur.|Pour définir cette option de manière dynamique, utilisez le mot clé **PAGETIMEOUT** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Lecture seule|Désigne la base de données comme lecture seulement.|Pour définir cette option de manière dynamique, utilisez le mot clé **READONLY** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sélectionnez Directory|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire contenant les fichiers que vous souhaitez accéder.<br /><br /> Lors de la définition d’un répertoire source de données spécifier l’annuaire où vos fichiers les plus couramment utilisés sont situés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez d’autres fichiers dans cet annuaire s’ils sont fréquemment utilisés. Vous pouvez également qualifier les noms de fichiers dans une déclaration SELECT avec le nom de l’annuaire :<br /><br /> SÉLECTIONNEZ \* À PARTIR DE C: 'MYDIR’EMP<br /><br /> Ou, vous pouvez spécifier un nouvel annuaire par défaut en utilisant la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sélectionnez Network Directory|Le chemin complet de l’annuaire contenant une base de données paradoxal, car il contient soit le fichier Pdoxusrs.net (dans Paradox 4.* x*) ou le fichier Paradox.net (dans Paradox 5.* x*). Si l’annuaire ne contient pas un de ces fichiers, le pilote Paradox en crée un. Pour plus d’informations sur ces fichiers, consultez la documentation Paradox.<br /><br /> Avant de pouvoir sélectionner un répertoire réseau, vous devez entrer votre nom d’utilisateur Paradox dans la boîte de texte **Nom de l’utilisateur.** Cliquez **sur Select Network Directory** pour sélectionner un répertoire réseau.|Pour définir cette option dynamiquement, utilisez le mot clé **PARADOXNETPATH** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|User Name|Le nom d’utilisateur Paradox. C’est le nom affiché à d’autres utilisateurs de fichiers Paradox lorsqu’un verrou est rencontré.|Pour définir cette option de manière dynamique, utilisez le mot clé **PARADOXUSERNAME** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
