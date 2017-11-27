---
title: "SQLXML n’est pas installé dans SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee759b9c94f2bbc8a7f0c8cb1595600f29959a87
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML n'est pas installé dans SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Avant de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 a été publiée avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et faisait partie de l’installation par défaut de tous les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions à l’exception de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. À partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la dernière version de SQLXML (SQLXML 4.0 SP1) n'est plus incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer SQLXML 4.0 SP1, téléchargez-le à partir de [emplacement d’installation de SQLXML 4.0 SP1](https://www.microsoft.com/en-us/download/details.aspx?id=30403).  
  
 Si une application s’exécute sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et nécessite SQLXML 4.0, vous devez télécharger et installer SQLXML 4.0 SP1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Comportement de SQLXML 4.0 SP1 avec les nouveaux types de données utilisant SQLOLEDB et le fournisseur OLE DB SQL Server Native Client  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]introduit les types de données suivants, qui permet aux développeurs à l’aide de SQLXML souhaiterez peut-être utiliser :  
  
-   **Date**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 Lors de l’utilisation de SQLXML 4.0 SP1 avec SQLOLEDB ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ces types s’affichent sous forme de chaînes à un développeur. SQLXML 4.0 SP1 activera ces quatre nouveaux types de données en tant que types scalaires intégrés lorsqu’il est utilisé avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Client OLE DB natif 11.0 ou version ultérieur. Tant que vous n'aurez pas téléchargé SQLXML 4.0 SP1, le mappage de ces types en types autres que chaîne risque de provoquer la troncation de certaines données. Par exemple, le mappage **DateTime2** à **xsd : date** données seront tronquées à la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** précision de 3,33 millisecondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de la programmation SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
