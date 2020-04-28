---
title: Accès aux types définis par l’utilisateur dans ADO.NET | Microsoft Docs
description: Les UDT, écrits en .NET Framework langages CLR, permettent à une base de données SQL Server de stocker des objets et des structures de données personnalisées. Dans ADO.NET, un fournisseur expose des UDT.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: d14205a6fb506f5d4fddaac1ab601ff1ee9205b8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488238"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accès aux types définis par l'utilisateur dans ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les types définis par l’utilisateur (UDT) sont écrits à l’aide de l’un [!INCLUDE[msCoName](../../includes/msconame-md.md)] des langages pris en charge par le .NET Framework Common Language Runtime (CLR) qui produit un code vérifiable. notamment [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Les types définis par l'utilisateur permettent de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les données sont exposées en tant que membres publics d'une classe ou d'une structure .NET Framework, et les comportements sont définis par des méthodes de la classe ou de la structure. Un type UDT peut être utilisé en tant que définition de colonne d’une table, en tant que variable dans un lot [!INCLUDE[tsql](../../includes/tsql-md.md)] ou en tant qu’argument d’une fonction ou d’une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Dans ADO.NET, le fournisseur **System. Data. SqlClient** expose des UDT de la manière suivante :  
  
-   Via **System. Data. SqlClient. SqlDataReader** en tant qu’objet.  
  
-   Dans le **SqlDataReader** comme octets bruts.  
  
-   En tant que paramètre d’un objet **System. Data. SqlClient. SqlParameter** .  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extraction de données UDT](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Décrit comment récupérer les données UDT et comment spécifier des paramètres.  
  
 [Mise à jour de colonnes UDT avec DataAdapters](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Décrit comment utiliser des UDT dans des **jeux** de données et comment mettre à jour des données UDT à l’aide de **DataAdapters**.  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR définis par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
