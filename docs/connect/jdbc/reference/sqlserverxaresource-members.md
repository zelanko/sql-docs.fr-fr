---
title: Membres de SQLServerXAResource | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 57004473ae83a98797992585baed5959e0874dcc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaresource-members"></a>Membres de SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Les tableaux suivants répertorient les membres exposés par le [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) classe.  
  
## <a name="constructors"></a>Constructeurs  
 Aucun.  
  
## <a name="fields"></a>Champs  
  
|Nom| Description|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)|Utilisé pour permettre les transactions XA étroitement couplées, qui ont des ID de transaction de branche XA (XID) différents mais le même ID de transaction global (GTRID).|  
  
## <a name="inherited-fields"></a>Champs hérités  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN, TMFAIL, TMJOIN, TMNOFLAGS, TMONEPHASE, TMRESUME, TMSTARTRSCAN, TMSUCCESS, TMSUSPEND, XA_OK, XA_RDONLY|  
  
## <a name="methods"></a>Méthodes  
  
|Nom| Description|  
|----------|-----------------|  
|[validation](../../../connect/jdbc/reference/commit-method-sqlserverxaresource.md)|Valide la transaction globale spécifiée par l’objet Xid donné.|  
|[fin](../../../connect/jdbc/reference/end-method-sqlserverxaresource.md)|Termine le travail effectué pour le compte d'une branche de transaction.|  
|[oubliez](../../../connect/jdbc/reference/forget-method-sqlserverxaresource.md)|Indique au gestionnaire de ressources de ne pas tenir compte d'une branche de transaction terminée de manière heuristique.|  
|[getTransactionTimeout](../../../connect/jdbc/reference/gettransactiontimeout-method-sqlserverxaresource.md)|Obtient la valeur de délai d’attente de transaction actuelle définie pour ce [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objet.|  
|[isSameRM](../../../connect/jdbc/reference/issamerm-method-sqlserverxaresource.md)|Détermine si l’instance du Gestionnaire de ressources représentée par l’objet cible est identique à l’instance du Gestionnaire de ressources représentée par l’objet XAResource donné.|  
|[préparer](../../../connect/jdbc/reference/prepare-method-sqlserverxaresource.md)|Demande que le Gestionnaire de ressources se préparer à une validation de la transaction spécifiée par l’objet Xid donné.|  
|[récupérer](../../../connect/jdbc/reference/recover-method-sqlserverxaresource.md)|Obtient une liste des branches de transactions préparées à partir d'un gestionnaire de ressources.|  
|[restauration](../../../connect/jdbc/reference/rollback-method-sqlserverxaresource.md)|Demande que le gestionnaire de ressources restaure le travail effectué pour le compte d'une branche de transaction.|  
|[setTransactionTimeout](../../../connect/jdbc/reference/settransactiontimeout-method-sqlserverxaresource.md)|Définit la valeur de délai d’attente de transaction en cours de ce [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) objet.|  
|[Démarrer](../../../connect/jdbc/reference/start-method-sqlserverxaresource.md)|Démarre le travail pour le compte d’une branche de transaction spécifiée dans l’objet Xid.|  
  
## <a name="inherited-methods"></a>Méthodes héritées  
  
|Classe héritée de :|Méthodes|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

