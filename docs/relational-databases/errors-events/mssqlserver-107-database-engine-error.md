---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8cc991f218748f0f6c4d35e915656847378c46cd
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver107"></a>MSSQLSERVER_107
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|107|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|P_NOCORRMATCH|  
|Texte du message|Le préfixe de colonne '%.*ls' ne correspond ni au nom de table ni au nom d'alias utilisés dans la requête.|  
  
## <a name="explanation"></a>Explication  
La liste de sélection de la requête contient un astérisque (*) incorrectement qualifié avec un préfixe de colonne. Cette erreur peut être retournée dans les conditions suivantes :  
  
-   Le préfixe de colonne ne correspond à aucun nom de table ou d'alias utilisé dans la requête. Par exemple, l'instruction suivante utilise un nom d'alias (`T1`) en tant que préfixe de colonne, mais l'alias n'est pas défini dans la clause FROM.  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   Un nom de table est spécifié en tant que préfixe de colonne alors qu'un nom d'alias pour la table est fourni dans la clause FROM. Par exemple, l'instruction suivante utilise le nom de table `ErrorLog` en tant que préfixe de colonne ; toutefois, la table a un alias (`T1`) défini dans la clause FROM.  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
    Si un alias a été fourni pour un nom de table dans la clause FROM, seul cet alias peut être utilisé pour préfixer des colonnes de la table.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Faites correspondre les préfixes de colonnes aux noms de tables ou d'alias spécifiés dans la clause FROM de la requête. Par exemple, les instructions ci-dessus peuvent être corrigées comme suit :  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
ou  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>Voir aussi  
[MSSQLSERVER_4104](~/relational-databases/errors-events/mssqlserver-4104-database-engine-error.md)  
  

