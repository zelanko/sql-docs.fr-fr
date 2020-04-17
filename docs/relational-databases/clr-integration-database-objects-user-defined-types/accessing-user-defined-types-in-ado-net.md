---
title: Accès aux types définis par l’utilisateur en ADO.NET Microsoft Docs
description: Les UDT, rédigés en langage .NET Framework CLR, permettent à une base de données SQL Server de stocker des objets et des structures de données personnalisées. Dans ADO.NET, un fournisseur expose les UDT.
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488238"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accès aux types définis par l'utilisateur dans ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les types définis par les utilisateurs (UDT) sont [!INCLUDE[msCoName](../../includes/msconame-md.md)] écrits à l’aide de l’une des langues prises en charge par le temps d’exécution de langage commun .NET Framework (CLR) qui produisent du code vérifiable. notamment [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. Les types définis par l'utilisateur permettent de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les données sont exposées en tant que membres publics d'une classe ou d'une structure .NET Framework, et les comportements sont définis par des méthodes de la classe ou de la structure. Un type UDT peut être utilisé en tant que définition de colonne d’une table, en tant que variable dans un lot [!INCLUDE[tsql](../../includes/tsql-md.md)] ou en tant qu’argument d’une fonction ou d’une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Dans ADO.NET, le fournisseur **System.Data.SqlClient** expose les UDT de la manière suivante :  
  
-   Par l’intermédiaire du **System.Data.SqlClient.SqlDataReader** comme objet.  
  
-   Par l’intermédiaire du **SqlDataReader** comme octets bruts.  
  
-   Comme paramètre d’un **objet System.Data.SqlClient.SqlParameter.**  
  
## <a name="in-this-section"></a>Dans cette section  
 [Extraction de données UDT](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Décrit comment récupérer les données UDT et comment spécifier des paramètres.  
  
 [Mise à jour de colonnes UDT avec DataAdapters](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Décrit comment travailler avec les UDT dans **DataSets** et comment mettre à jour les données UDT à l’aide **de DataAdapters**.  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR définis par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
