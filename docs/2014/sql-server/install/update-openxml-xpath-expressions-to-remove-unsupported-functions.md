---
title: Mettre à jour les expressions XPath OPENXML pour supprimer les fonctions non prises en charge | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041765"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a>Mettre à jour les expressions OPENXML XPath pour supprimer les fonctions non prises en charge
  Le Conseiller de mise à niveau a détecté l'utilisation de la fonctionnalité XPath. Vous risquez de subir les effets des modifications apportées à XPath au niveau des fonctionnalités OPENXML après la mise à niveau.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 MSXML 3.0 est à présent le moteur sous-jacent qui sert à traiter les expressions XPath utilisées à l'intérieur des requêtes OPENXML. MSXML 3.0 possède un moteur XPath 1.0 plus strict qui ne prend plus en charge les fonctions suivantes :  
  
-   format-number()  
  
-   formatNumber()  
  
-   current()  
  
-   element-available()  
  
-   function-available()  
  
-   system-property()  
  
## <a name="corrective-action"></a>Action corrective  
 Pour format-number() et formatNumber(), vous pouvez utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour les autres fonctions présentées précédemment qui ne sont plus prises en charge, il n'existe pas de solution de remplacement directe.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
