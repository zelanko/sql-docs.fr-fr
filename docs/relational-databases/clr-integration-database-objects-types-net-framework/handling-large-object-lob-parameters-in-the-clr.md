---
title: Gestion des paramètres Large Object (LOB) dans le CLR | Microsoft Docs
description: Cet article explique comment gérer les valeurs d’objets volumineux (LOB) pour les paramètres dans SQL Server intégration du CLR. Utilisez SqlBytes et SqlChars pour les types LOB.
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
ms.openlocfilehash: 0941ca2f5fc1a05397dd3dbec5e0dd27c6e5d815
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488447"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestion des paramètres LOB dans le CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilisez **SqlBytes** et **SqlChars** pour passer les paramètres de type binaire LOB (objet BLOB) (**varbinary (max)**) et de type de caractère LOB (**nvarchar (max)**), respectivement. Ces types autorisent la diffusion en continu des valeurs LOB de la base de données à la routine CLR (Common Language Runtime), au lieu de copier la valeur entière dans l'espace managé. **SqlBinary** et **SqlString** ne doivent être utilisés que pour les petites valeurs binaires et de chaîne de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server dans le .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
