---
title: Types CLR volumineux définis par l’utilisateur | Microsoft Docs
description: Types CLR volumineux définis par l’utilisateur dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: f152e497fd1a19924321580280e520598773081d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018037"
---
# <a name="large-clr-user-defined-types"></a>Types CLR volumineux définis par l'utilisateur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dans SQL Server 2005, les types définis par l'utilisateur (UDT) dans le CLR (Common Language Runtime) se limitaient à une taille de 8 000 octets. Cette limite n'est plus d'actualité dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et versions ultérieures. Les types CLR définis par l'utilisateur sont désormais traités de la même manière que les objets LOB. Ainsi, les types définis par l'utilisateur dont la taille est inférieure ou égale à 8 000 octets adoptent le même comportement que dans SQL Server 2005 mais les types définis par l'utilisateur plus volumineux sont pris en charge et affichent une taille « illimitée ».  
  
 Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;OLE DB&#41;](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md).  
  
## <a name="use-cases"></a>Cas d'usage   
  
 Pour OLE DB, la prise en charge des types définis par l’utilisateur volumineux offre la possibilité de diffuser des valeurs UDT vers et depuis le serveur au moyen d’une liaison ISequentialStream.  
  
 Les types définis par l'utilisateur dont la taille est inférieure ou égale à 8 000 octets se comporteront de la même manière que dans SQL Server 2005. Pour OLE DB, vous pouvez toujours transmettre en continu petits types UDT à l’aide de liaison ISequentialStream.  
  
 Le code natif doit quelquefois comprendre le contenu des types CLR définis par l'utilisateur mais n'a pas besoin d'instancier les objets managés. Dans ce cas, vous pouvez utiliser la sérialisation personnalisée pour convertir des valeurs de type défini par l'utilisateur (UDT) sur le serveur dans un format bien connu des clients.  
  
 Pour les applications qui disposent d'un code d'accès aux données existant, vous pouvez exploiter le comportement des types CLR définis par l'utilisateur sur le client en extrayant des types définis par l'utilisateur via des API natives et en les instanciant au moyen de l'interopérabilité C++/CLI dans des applications en mode mixte.  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
