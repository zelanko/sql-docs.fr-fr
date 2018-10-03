---
title: Définition des Options par programmation pour le pilote Paradox | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50862270598172f8ff9e8572e9f201cbeb826bc5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637237"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Définition d’options par programmation pour le pilote Paradox
|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Répertoire|Définit le répertoire cible.|Pour définir cette option de manière dynamique, utilisez le **DEFAULTDIR** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Séquence de classement|La séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être ASCII (la valeur par défaut), International, suédois-finnois ou Norvégien-Danois.|Pour définir cette option de manière dynamique, utilisez le **COLLATINGSEQUENCE** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Description|Une description facultative des données dans la source de données ; par exemple, « date d’embauche, historique de salaire et examen actuel de tous les employés. »|Pour définir cette option de manière dynamique, utilisez le **DESCRIPTION** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exclusive|Si le **exclusif** est activée, la base de données s’ouvre en mode exclusif et est accessible par un seul utilisateur à la fois. Les performances sont améliorées lors de l’exécution en mode exclusif.|Pour définir cette option de manière dynamique, utilisez le **exclusif** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Style de réseau|Le style d’accès réseau à utiliser lors de l’accès aux données Paradox : soit « 3.*x*» pour Paradox 3. *x* ou « 4. *x*» pour Paradox 4. *x* ou 5. *x*. Peut être défini sur « 3. *x*» ou « 4. *x*» si la version est Paradox 4. *x* ou 5. *x*; si la version est Paradox 3. *x*, le style doit être « 3. *x*».|Pour définir cette option de manière dynamique, utilisez le **PARADOXNETSTYLE** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Délai d’expiration de la page|Spécifie la période de temps, en dixièmes de seconde, une page (si non utilisé) reste dans la mémoire tampon avant d’être supprimés. La valeur par défaut est 600 dixièmes de seconde (60 secondes). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’expiration de la page ne peut pas être 0 en raison d’un délai intrinsèque. Le délai d’expiration de la page ne peut pas être inférieure au délai inhérent, même si l’option de délai d’attente de page est définie en dessous de cette valeur.|Pour définir cette option de manière dynamique, utilisez le **PAGETIMEOUT** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le **READONLY** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sélectionnez le répertoire|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire contenant les fichiers que vous souhaitez accéder.<br /><br /> Lorsque la définition d’un répertoire de source de données spécifiez le répertoire où le plus couramment utilisés fichiers se trouvent. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire si elles sont utilisées fréquemment. Ou bien, vous pouvez qualifier les noms de fichiers dans une instruction SELECT avec le nom du répertoire :<br /><br /> SÉLECTIONNEZ \* À PARTIR DE C:\MYDIR\EMP<br /><br /> Ou, vous pouvez spécifier un répertoire par défaut à l’aide de la **SQLSetConnectOption** fonction avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le **DEFAULTDIR** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sélectionnez le répertoire réseau|Le chemin d’accès complet du répertoire contenant une base de données de verrou Paradox, car il contient le fichier Pdoxusrs.net (dans Paradox 4. *x*) ou le fichier Paradox.net (dans Paradox 5. *x*). Si le répertoire ne contient pas un de ces fichiers, le pilote Paradox en crée un. Pour plus d’informations sur ces fichiers, consultez la documentation de Paradox.<br /><br /> Avant de pouvoir sélectionner un répertoire réseau, vous devez entrer votre nom d’utilisateur Paradox dans le **nom d’utilisateur** zone de texte. Cliquez sur **sélectionner un répertoire réseau** pour sélectionner un répertoire réseau.|Pour définir cette option de manière dynamique, utilisez le **PARADOXNETPATH** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Nom d'utilisateur|Le nom d’utilisateur Paradox. Il s’agit du nom affiché à d’autres utilisateurs des fichiers Paradox lorsqu’un verrou est rencontré.|Pour définir cette option de manière dynamique, utilisez le **PARADOXUSERNAME** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
