---
title: Quand utiliser SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7cc9a06601ed0819457b9348bb10cb33b4b92d37
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62637912"
---
# <a name="when-to-use-sql-server-native-client"></a>Quand utiliser SQL Server Native Client
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est une technologie que vous pouvez utiliser pour accéder aux données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Pour en savoir plus sur les différentes technologies d’accès aux données, consultez [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Lorsque vous décidez s'il faut utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client comme technologie d'accès aux données de votre application, vous devez considérer plusieurs facteurs.  
  
 Pour les nouvelles applications, si vous utilisez un langage de programmation managé tel que Microsoft Visual C# ou Visual Basic et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui fait partie du .NET Framework.  
  
 Si vous développez une application COM et que vous devez accéder aux nouvelles fonctionnalités introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Si vous n'avez pas besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC (Windows Data Access Components).  
  
 Pour les applications OLE DB et ODBC existantes, vous devez décider principalement si vous avez besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous possédez une application déjà rodée qui n'a pas besoin des nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC. Toutefois, si vous devez accéder à ces nouvelles fonctionnalités, telles que le [type de données XML](/sql/t-sql/xml/xml-transact-sql), vous devez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utiliser Native Client.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client et MDAC prennent en charge l'isolation de la transaction de lecture validée à l'aide du contrôle de version de ligne, mais seul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge l'isolation de la transaction d'instantané. (En termes de programmation, l'isolation des transactions de lecture validée avec le contrôle de version de ligne équivaut à la transaction de lecture validée.)  
  
 Pour plus d’informations sur les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] différences entre Native Client et MDAC, consultez [mise à jour d’une application vers SQL Server Native Client à partir de MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Rubriques de procédures relatives à ODBC](../native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Rubriques "Comment" relatives aux OLE DB](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
