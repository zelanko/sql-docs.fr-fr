---
title: Prise en charge de FOR XML pour les types de données définis par l’utilisateur (UDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e608244e1d22e4482534c1658006cba4650d0083
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889045"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Prise en charge de FOR XML pour les types de données définis par l'utilisateur (UDT)
  FOR XML ne prend pas en charge les types de données définis par l'utilisateur (UDT) du Common Language Runtime (CLR).  
  
 Pour utiliser FOR XML avec des types de données CLR définis par l'utilisateur, assurez-vous que le type de données a une sérialisation XML et utilisez un cast explicite en XML dans la clause select FOR XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge FOR XML des différents types de données SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
