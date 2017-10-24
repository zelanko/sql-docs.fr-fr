---
title: "Cancel (méthode) (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba15f12006b31fa8ce0f67fd14ef7c6afb46863b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cancel-method-ado"></a>Cancel (méthode) (ADO)
Annule l’exécution d’un appel de méthode asynchrone en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez le **Annuler** méthode pour terminer l’exécution d’un appel de méthode asynchrone : autrement dit, une méthode est appelée avec le **adAsyncConnect**, **adAsyncExecute**, ou **adAsyncFetch** option.  
  
 Le tableau suivant indique quelle tâche est terminée lorsque vous utilisez la **Annuler** méthode sur un type d’objet particulier.  
  
|Si *objet* est un|Le dernier appel asynchrone à cette méthode se termine.|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[Exécuter](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Connexion](../../../ado/reference/ado-api/connection-object-ado.md)|[Exécutez](../../../ado/reference/ado-api/execute-method-ado-connection.md) ou [ouvert](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[Enregistrement](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), ou [ouvert](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md)|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Flux de données](../../../ado/reference/ado-api/stream-object-ado.md)|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Objet de commande (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Objet d’enregistrement (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Objet de flux de données (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de méthode Cancel (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [Exemple de méthode Cancel (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Exemple de méthode Cancel (VC ++)](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel (méthode) (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Execute (méthode) (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [Execute (méthode) (connexion ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open (méthode) (connexion ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open (méthode) (jeu d’enregistrements ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)

