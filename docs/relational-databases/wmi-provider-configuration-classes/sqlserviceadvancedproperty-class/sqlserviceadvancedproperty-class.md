---
title: Classe SqlServiceAdvancedProperty | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SqlServiceAdvancedProperty Class
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SqlServiceAdvancedProperty class
ms.assetid: a5d06bde-6058-464c-a4aa-444d83f2331f
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc15b15084f74c6749c1c3a33b34beadcb82d0a1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlserviceadvancedproperty-class"></a>Classe SqlServiceAdvancedProperty
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Le [classe SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) représente une propriété avancée du service qui est référencé par le [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) objet.  
  
 Le [advancedproperties, propriété (classe SqlService)](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/advancedproperties-property-sqlservice-class.md) fait référence à un tableau de [classe SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) objets.  
  
 Le [démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx) classe représente des propriétés qui sont uniques au service. Ces propriétés ne sont pas dans la liste des propriétés qui est associé à la [classe SqlService](http://technet.microsoft.com/library/ms186497.aspx) classe. Le [classe SqlServiceAdvancedProperty](http://technet.microsoft.com/library/ms182447.aspx) classe permet la représentation sous forme de propriétés de chaîne, numérique ou booléenne. Vous pouvez utiliser cette classe pour afficher les propriétés uniques du service spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Services de démarrage, arrêt et interruption](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
