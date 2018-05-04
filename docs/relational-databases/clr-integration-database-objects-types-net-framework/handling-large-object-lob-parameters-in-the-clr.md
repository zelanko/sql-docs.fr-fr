---
title: Gestion des paramètres LOB (Large Object) dans le CLR | Documents Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d6c7028471d37362e8105f327d6a77aa39182bcb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestion des paramètres LOB dans le CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilisez **SqlBytes** et **SqlChars** pour passer les type binaire LOB (large object) (**varbinary (max)**) et le type de caractère LOB (**nvarchar (max)**) paramètres, respectivement. Ces types autorisent la diffusion en continu des valeurs LOB de la base de données à la routine CLR (Common Language Runtime), au lieu de copier la valeur entière dans l'espace managé. **SqlBinary** et **SqlString** doit être utilisé uniquement pour les petite binaire et les valeurs de chaîne de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
