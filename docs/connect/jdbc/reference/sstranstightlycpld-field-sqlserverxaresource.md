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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8129cf30a7ba95c39281c9ff4bd2a5c0eac4183c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818417"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Champ SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Utilisé pour permettre les transactions XA étroitement couplées, qui ont des ID de transaction de branche XA (XID) différents mais le même ID de transaction global (GTRID).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Valeur de champ  
 Un **int** valeur de 32 768.  
  
## <a name="remarks"></a>Notes   
 Chaque transaction est identifiée par un ID de transaction de branche XA (XID) et un ID de transaction global (GTRID). Pour permettre aux applications d’utiliser des transactions XA étroitement couplées, qui ont des XID différents mais le même GTRID, vous devez définir [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) selon le paramètre flags de la méthode XAResource.start. Pour plus d’informations sur l’utilisation de cet indicateur, consultez [présentation des Transactions XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerXAResource, champs](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource, membres](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
