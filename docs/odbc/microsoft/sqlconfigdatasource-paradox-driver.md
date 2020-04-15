---
title: SQLConfigDataSource (Pilote Paradox) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLConfigDataSource
ms.assetid: 59e84c4e-debe-49d7-b97b-84c736b0c793
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68e60d7ca9c37865c1b265297d24591638a44965
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283929"
---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (pilote Paradox)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Paradox Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 La fonction **SQLConfigDataSource** qui est utilisée pour ajouter, modifier ou supprimer une source de données utilise dynamiquement les mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|La séquence dans laquelle les champs sont triés.<br /><br /> Lorsque le pilote Paradox est utilisé, la séquence peut être ASCII (par défaut), Internationale, suédoise-finlandaise ou norvégienne-danoise.<br /><br /> Cela définit la même option que **Collating Sequence** dans la boîte de dialogue de configuration.|  
|DBQ|Le nom du fichier de base de données.<br /><br /> Cela définit la même option que **la base de données** dans la boîte de dialogue de configuration.|  
|DÉFAUTDIR|Le parcours du répertoire.|  
|Description|Une description des données dans la source de données.<br /><br /> Cela définit la même option que **description** dans la boîte de dialogue de configuration.|  
|DRIVER|La spécification de chemin au conducteur DLL.|  
|DRIVERID (EN)|Une pièce d’identité pour le conducteur.<br /><br /> 26 (Paradoxe 3.x)<br /><br /> 282 (Paradoxe 4.x)<br /><br /> 538 (Paradoxe 5.x)|  
|Exclusive|Détermine si la base de données sera ouverte en mode exclusif (accessible par un seul utilisateur à la fois) ou en mode partagé (accessible par plus d’un utilisateur à la fois). Peut être vrai (mode exclusif) ou faux (mode partagé).<br /><br /> Cela définit la même option que **Exclusive** dans la boîte de dialogue de configuration.|  
|FIL (EN)|Type de fichier Paradox 3.x, Paradox 4.x, ou Paradox 5.x|  
|Filetype|Type de fichier pour le pilote de texte (Texte).|  
|PAGETIMEOUT|Spécifie la période de temps, en dixièmes de seconde, qu’une page (si elle n’est pas utilisée) reste dans le tampon avant d’être supprimée. La valeur par défaut est de 600 dixièmes de seconde (60 secondes). Notez que cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Cela définit la même option que **Page Timeout** dans la boîte de dialogue de configuration.|  
|PARADOXNETPATH|Le chemin complet de l’annuaire contenant une base de données paradoxal, car il contient soit le fichier PDOXUSRS.net (dans Paradox 4.* x*) ou le fichier PARADOX.net (dans Paradox 5.* x*). Si l’annuaire ne contient pas un de ces fichiers, le pilote Paradox en crée un. Pour plus d’informations sur ces fichiers, consultez la documentation Paradox.<br /><br /> Avant qu’un répertoire réseau puisse être sélectionné, un nom d’utilisateur Paradox doit être entré.<br /><br /> Cela définit la même option que **Select Network Directory** dans la boîte de dialogue de configuration.|  
|PARADOXNETSTYLE|Pour le pilote Paradox, le style d’accès réseau à utiliser lors de l’accès aux données Paradox : soit « 3.x » pour Paradox 3. *x* ou "4.x" pour Paradox 4. *x* ou 5. *x*. Peut être réglé à "3.x" ou "4.x" si la version est Paradox 4. *x* ou 5. *x*; si la version est Paradox 3. *x*, le style doit être "3.x".<br /><br /> Cela définit la même option que **Net Style** dans la boîte de dialogue de configuration.|  
|PARADOXUSERNAME|Pour le pilote Paradox, le nom d’utilisateur Paradox.<br /><br /> Cela définit la même option que **le nom d’utilisateur** dans la boîte de dialogue de configuration.|  
|PWD|Mot de passe.<br /><br /> Il s’agit d’un mot clé facultatif et ne sera jamais écrit au fichier par le conducteur. Il est utilisé dans un appel à **SQLDriverConnect** contre les fichiers Paradox sécurisés par mot de passe. Le mot de passe utilisé sera valide chaque fois qu’une table est ouverte. Si aucun mot de passe n’est passé dans la chaîne de connexion, aucun mot de passe n’est établi pour cette table. Si les tables ont des mots de passe différents, plus d’un ne peut pas être ouvert dans la même session, ni les tables ne peuvent être jointes.|  
|READONLY|VRAI pour faire lecture de fichier seulement; FALSE pour faire fichier non lu seulement.<br /><br /> Cela définit la même option que **Lire uniquement** dans la boîte de dialogue de configuration.|  
|Fils|Le nombre de fils d’arrière-plan pour le moteur à utiliser. Cette valeur est de 3, et ne peut pas être changée.<br /><br /> Cela définit la même option que **Threads** dans la boîte de dialogue de configuration.|
