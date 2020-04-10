---
title: Champ SSTRANSTIGHTLYCPLD (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6d816ba896b792894716b9b61b133d1acea0c93
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925650"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Champ SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Utilisé pour permettre les transactions XA étroitement couplées, qui ont des ID de transaction de branche XA (XID) différents mais le même ID de transaction global (GTRID).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Valeur de champ  
 Une valeur **int** de 32768.  
  
## <a name="remarks"></a>Notes  
 Chaque transaction est identifiée par un ID de transaction de branche XA (XID) et un ID de transaction global (GTRID). Pour permettre aux applications d’utiliser des transactions XA étroitement couplées, qui ont des XID différents mais le même GTRID, vous devez définir [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) selon le paramètre flags de la méthode XAResource.start. Pour plus d'informations sur l’utilisation de cet indicateur, consultez [Compréhension des transactions XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, champs](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
