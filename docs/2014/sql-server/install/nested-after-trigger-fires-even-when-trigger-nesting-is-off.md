---
title: Un déclencheur AFTER imbriqué déclenche même lorsque l’imbrication du déclencheur est OFF | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DML triggers, nested
- nested triggers option
- triggers [SQL Server], nested
ms.assetid: 94d72960-676e-40d9-81bc-08bffe778110
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f53e478c212793c6798f0fcabbf00cb1486134d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038990"
---
# <a name="nested-after-trigger-fires-even-when-trigger-nesting-is-off"></a>Un déclencheur AFTER imbriqué est exécuté même lorsque l'imbrication du déclencheur est OFF
  Le Conseiller de mise à niveau a détecté un déclencheur AFTER imbriqué à l'intérieur d'un déclencheur INSTEAD OF défini sur une ou plusieurs tables. Les déclencheurs imbriqués AFTER peuvent s'exécuter même lorsque l'option de configuration du serveur `nested triggers` a la valeur 0.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Le premier déclencheur AFTER imbriqué dans un déclencheur INSTEAD OF se déclenche même si l'option de configuration du serveur `nested triggers` est définie à 0. Toutefois, les déclencheurs AFTER suivants ne se déclenchent pas sous ce paramètre.  
  
## <a name="corrective-action"></a>Action corrective  
 Contrôlez les déclencheurs imbriqués de vos applications afin de déterminer si ces applications sont toujours conformes aux règles d'entreprise relatives à ce nouveau comportement lorsque l'option de configuration du serveur de `nested triggers` est définie à 0, puis effectuez les modifications nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
