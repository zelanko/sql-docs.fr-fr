---
title: Membres de SQLServerXAResource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b420dd7c4bc714e26c8078112c5af54ae5aa7b0c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67970069"
---
# <a name="sqlserverxaresource-members"></a>Membres de SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants présentent les membres exposés par la classe [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md).  
  
## <a name="constructors"></a>Constructeurs  
 Aucun.  
  
## <a name="fields"></a>Champs  
  
|Name|Description|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)|Utilisé pour permettre les transactions XA étroitement couplées, qui ont des ID de transaction de branche XA (XID) différents mais le même ID de transaction global (GTRID).|  
  
## <a name="inherited-fields"></a>Champs hérités  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN, TMFAIL, TMJOIN, TMNOFLAGS, TMONEPHASE, TMRESUME, TMSTARTRSCAN, TMSUCCESS, TMSUSPEND, XA_OK, XA_RDONLY|  
  
## <a name="methods"></a>Méthodes  
  
|Name|Description|  
|----------|-----------------|  
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverxaresource.md)|Valide la transaction globale spécifiée par l’objet Xid donné.|  
|[end](../../../connect/jdbc/reference/end-method-sqlserverxaresource.md)|Termine le travail effectué pour le compte d'une branche de transaction.|  
|[forget](../../../connect/jdbc/reference/forget-method-sqlserverxaresource.md)|Indique au gestionnaire de ressources de ne pas tenir compte d'une branche de transaction terminée de manière heuristique.|  
|[getTransactionTimeout](../../../connect/jdbc/reference/gettransactiontimeout-method-sqlserverxaresource.md)|Récupère la valeur du délai d’expiration actuel des transactions définie pour cet objet [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md).|  
|[isSameRM](../../../connect/jdbc/reference/issamerm-method-sqlserverxaresource.md)|Détermine si l’instance de gestionnaire de ressources représentée par l’objet cible est identique à celle qui est représentée par l’objet XAResource donné.|  
|[prepare](../../../connect/jdbc/reference/prepare-method-sqlserverxaresource.md)|Demande au gestionnaire de ressources de se préparer à une validation de la transaction spécifiée par l’objet Xid donné.|  
|[recover](../../../connect/jdbc/reference/recover-method-sqlserverxaresource.md)|Obtient une liste des branches de transactions préparées à partir d'un gestionnaire de ressources.|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverxaresource.md)|Demande que le gestionnaire de ressources restaure le travail effectué pour le compte d'une branche de transaction.|  
|[setTransactionTimeout](../../../connect/jdbc/reference/settransactiontimeout-method-sqlserverxaresource.md)|Définit la valeur du délai d’expiration actuel des transactions de cet objet [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md).|  
|[start](../../../connect/jdbc/reference/start-method-sqlserverxaresource.md)|Commence le travail pour le compte d’une branche de transaction spécifiée dans l’objet Xid.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
