---
title: SQLXML n’est pas installé dans SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7561d2d22439112ea084f1f8a62c32aeb5591cfc
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59240757"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML n'est pas installé dans SQL Server
  Avant [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 était fourni avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et faisait partie de l'installation par défaut de toutes les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l'exception de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. À partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la dernière version de SQLXML (SQLXML 4.0 SP1) n'est plus incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer SQLXML 4.0 SP1 lorsqu’il est disponible, téléchargez-le à partir de [emplacement d’installation de SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=16978).  
  
 Si une application est exécutée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et nécessite SQLXML 4.0, et si l'ordinateur ne dispose pas de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], vous devez télécharger et installer SQLXML 4.0 SP1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Comportement de SQLXML 4.0 SP1 avec les nouveaux types de données utilisant SQLOLEDB et le fournisseur OLE DB SQL Server Native Client  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduit les types de données suivants, que les développeurs à l’aide de SQLXML souhaiterez peut-être utiliser :  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 Lors de l'utilisation de SQLXML 4.0 SP1 avec SQLOLEDB (issu de Windows Data Access Components, anciennement connu sous le nom Microsoft Data Access Components) ou le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ces nouveaux types apparaîtront au développeur sous la forme de chaînes. SQLXML 4.0 SP1 activera ces quatre nouveaux types de données sous la forme de types scalaires intégrés lors d'une utilisation avec le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider 11.0. Tant que vous n'aurez pas téléchargé SQLXML 4.0 SP1, le mappage de ces types en types autres que chaîne risque de provoquer la troncation de certaines données. Par exemple, mappage `DateTime2` à `xsd:date` entraîne des données seront tronquées à la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` précision de 3,33 millisecondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de la programmation SQLXML 4.0](sqlxml-4-0-programming-concepts.md)  
  
  
