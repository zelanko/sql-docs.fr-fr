---
title: Close, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Close
- _Stream::Close
- _Record::Close
helpviewer_keywords:
- Close method [ADO]
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8a1d153d1433a377bb488366111b75a986365132
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919931"
---
# <a name="close-method-ado"></a>Close, méthode (ADO)
Ferme un objet ouvert et tous les objets dépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode **Close** pour fermer une [connexion](../../../ado/reference/ado-api/connection-object-ado.md), un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md)ou un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) pour libérer toutes les ressources système associées. La fermeture d’un objet ne le supprime pas de la mémoire ; vous pouvez modifier ses paramètres de propriété et l’ouvrir à nouveau ultérieurement. Pour éliminer complètement un objet de la mémoire, fermez l’objet, puis affectez à la variable objet la valeur *Nothing* (dans Visual Basic).  
  
## <a name="connection"></a>Connexion  
 L’utilisation de la méthode **Close** pour fermer un objet **Connection** ferme également tous les objets **Recordset** actifs associés à la connexion. Un objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) associé à l’objet de **connexion** que vous fermez est conservé, mais il n’est plus associé à un objet de **connexion** ; autrement dit, sa propriété [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) prend la valeur **Nothing**. En outre, la collection de [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) de l’objet de **commande** est effacée de tous les paramètres définis par le fournisseur.  
  
 Vous pouvez appeler ultérieurement la méthode [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) pour rétablir la connexion à la même source de données, ou à une autre. Pendant la fermeture de l’objet de **connexion** , l’appel de toutes les méthodes qui requièrent une connexion ouverte à la source de données génère une erreur.  
  
 La fermeture d’un objet de **connexion** pendant l’existence d’objets **Recordset** ouverts sur la connexion annule toutes les modifications en attente dans tous les objets **Recordset** . La fermeture explicite d’un objet **Connection** (en appelant la méthode **Close** ) pendant qu’une transaction est en cours génère une erreur. Si un objet de **connexion** se trouve hors de portée pendant qu’une transaction est en cours, ADO annule automatiquement la transaction.  
  
## <a name="recordset-record-stream"></a>Recordset, enregistrement, flux  
 L’utilisation de la méthode **Close** pour fermer un objet **Recordset**, **Record**ou **Stream** libère les données associées et tout accès exclusif que vous pouvez avoir pour les données via cet objet particulier. Vous pouvez appeler ultérieurement la méthode [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) pour rouvrir l’objet avec les mêmes attributs, ou modifiés.  
  
 Lors de la fermeture d’un objet **Recordset** , l’appel de toute méthode nécessitant un curseur dynamique génère une erreur.  
  
 Si une modification est en cours alors qu’elle est en mode de mise à jour immédiate, l’appel de la méthode **Close** génère une erreur. au lieu de cela, appelez d’abord la méthode [Update](../../../ado/reference/ado-api/update-method.md) ou [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) . Si vous fermez l’objet **Recordset** en mode de mise à jour par lot, toutes les modifications apportées depuis le dernier appel [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) sont perdues.  
  
 Si vous utilisez la méthode [clone](../../../ado/reference/ado-api/clone-method-ado.md) pour créer des copies d’un objet **Recordset** ouvert, la fermeture de l’original ou d’un clone n’a aucune incidence sur les autres copies.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Open et Close, exemple de méthodes (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open et Close, exemple de méthode (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open et Close, exemple de méthodes (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open, méthode (connexion ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
