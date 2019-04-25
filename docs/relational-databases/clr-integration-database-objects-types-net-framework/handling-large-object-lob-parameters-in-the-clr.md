---
title: Gestion des paramètres LOB (Large Object) dans le CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6079766625633391e281b99751ba42bb772531e3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760471"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestion des paramètres LOB dans le CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilisez **SqlBytes** et **SqlChars** pour passer de type binaire LOB (large object) (**varbinary (max)**) et le type de caractère LOB (**nvarchar (max)**) paramètres, respectivement. Ces types autorisent la diffusion en continu des valeurs LOB de la base de données à la routine CLR (Common Language Runtime), au lieu de copier la valeur entière dans l'espace managé. **SqlBinary** et **SqlString** doit être utilisé uniquement pour les petites binaire et de valeurs de chaîne de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
