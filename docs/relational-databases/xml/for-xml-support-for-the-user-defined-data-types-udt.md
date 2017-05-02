---
title: "Prise en charge de FOR XML pour les types de données définis par l’utilisateur (UDT) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1d47d9e39b1b797a3c7022c722e61fbbfb932710
ms.lasthandoff: 04/11/2017

---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Prise en charge de FOR XML pour les types de données définis par l'utilisateur (UDT)
  FOR XML ne prend pas en charge les types de données définis par l'utilisateur (UDT) du Common Language Runtime (CLR).  
  
 Pour utiliser FOR XML avec des types de données CLR définis par l'utilisateur, assurez-vous que le type de données a une sérialisation XML et utilisez un cast explicite en XML dans la clause select FOR XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge FOR XML des différents types de données SQL Server](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
