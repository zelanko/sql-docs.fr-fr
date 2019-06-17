---
title: Gestion des paramètres LOB (Large Object) dans le CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 09797eac229a4b3b92f94a60b6e1c06c9ec12f08
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919504"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestion des paramètres LOB dans le CLR
  Utilisez `SqlBytes` et `SqlChars` pour passer des paramètres de type binaire LOB (`varbinary(max)`) et de type caractère LOB (`nvarchar(max)`), respectivement. Ces types autorisent la diffusion en continu des valeurs LOB de la base de données à la routine CLR (Common Language Runtime), au lieu de copier la valeur entière dans l'espace managé. `SqlBinary` et `SqlString` doivent être utilisés uniquement pour les valeurs des petites chaînes binaires et des chaînes de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
