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
manager: jroth
ms.openlocfilehash: e692e8853417abae386ac151eca4b49f11b12f02
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698999"
---
# <a name="close-method-ado"></a>Close, méthode (ADO)
Ferme un objet ouvert et tous les objets dépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>Notes  
 Utilisez le **fermer** méthode pour fermer un [connexion](../../../ado/reference/ado-api/connection-object-ado.md), un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), ou un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet pour libérer les ressources système associées. Fermeture d’un objet ne le supprime pas de la mémoire. Vous pouvez modifier ses paramètres de propriété et ouvrez à nouveau ultérieurement. Pour éliminer complètement un objet de la mémoire, fermer l’objet et définissez la variable objet *rien* (en Visual Basic).  
  
## <a name="connection"></a>Connexion  
 À l’aide de la **fermer** méthode pour fermer un **connexion** objet ferme également tout active **Recordset** objets associés à la connexion. Un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet associé à la **connexion** objet que vous fermez est conservé, mais il sera n’est plus associé un **connexion** objet ; autrement dit, son [ ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété sera définie **rien**. En outre, le **commande** l’objet [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) seront supprimés la collection de tous les paramètres définis par le fournisseur.  
  
 Vous pouvez appeler ultérieurement la [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode pour rétablir la connexion à la même source de données ou à un autre, source de données. Bien que le **connexion** objet est fermé, appelez des méthodes qui requièrent une connexion ouverte à la source de données génère une erreur.  
  
 Fermeture un **connexion** quand il sont ouverts de l’objet **Recordset** objets sur la connexion annule toutes les modifications en attente dans tous les **Recordset** objets. Fermer explicitement un **connexion** objet (appelant le **fermer** méthode) pendant qu’une transaction est en cours génère une erreur. Si un **connexion** objet se situe hors de portée lorsqu’une transaction est en cours, ADO restaure automatiquement la transaction.  
  
## <a name="recordset-record-stream"></a>Jeu d’enregistrements, enregistrement, Stream  
 À l’aide de la **fermer** méthode pour fermer un **Recordset**, **enregistrement**, ou **Stream** objet libère les données associées et tout accès exclusif vous avez peut-être dû les données via cet objet spécifique. Vous pouvez appeler ultérieurement la [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode pour rouvrir l’objet avec le même ou modifiées, des attributs.  
  
 Pendant un **Recordset** objet est fermé, appelez des méthodes qui requièrent un curseur dynamique génère une erreur.  
  
 Si une modification est en cours d’exécution en mode de mise à jour immédiate, l’appel la **fermer** méthode génère une erreur ; au lieu de cela, appelez le [mettre à jour](../../../ado/reference/ado-api/update-method.md) ou [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) méthode première. Si vous fermez le **Recordset** de l’objet en mode batch mise à jour, toutes les modifications depuis le dernier [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) appel sont perdues.  
  
 Si vous utilisez le [Clone](../../../ado/reference/ado-api/clone-method-ado.md) méthode pour créer des copies ouvert **Recordset** l’objet, la fermeture de la version d’origine ou un clone n’affecte pas les autres copies.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Les méthodes Open et Close, exemple (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Les méthodes Open et Close, exemple (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Les méthodes Open et Close, exemple (VC ++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
