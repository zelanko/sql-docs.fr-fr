---
title: Prise en charge de FOR XML pour les types de données définis par l’utilisateur (UDT) | Microsoft Docs
description: Découvrez la prise en charge des types de données définis par l’utilisateur (UDT) lors de l’utilisation de la clause FOR XML.
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 53a70da583b55fa8d979aeaaee3782fd6551c6ea
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729924"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Prise en charge de FOR XML pour les types de données définis par l'utilisateur (UDT)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  FOR XML ne prend pas en charge les types de données définis par l'utilisateur (UDT) du Common Language Runtime (CLR).  
  
 Pour utiliser FOR XML avec des types de données CLR définis par l'utilisateur, assurez-vous que le type de données a une sérialisation XML et utilisez un cast explicite en XML dans la clause select FOR XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de FOR XML pour différents types de données SQL Server](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
