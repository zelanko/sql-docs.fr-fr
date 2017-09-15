---
title: "Propriété du fournisseur (ADO) | Documents Microsoft"
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
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1839d8bc9c954d3f5ceeafca2b604304801f643f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="provider-property-ado"></a>Propriété du fournisseur (ADO)
Indique le nom du fournisseur pour un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui indique le nom du fournisseur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **fournisseur** propriété pour définir ou retourner le nom du fournisseur pour une connexion. Cette propriété peut également être définie en fonction du contenu de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété ou le *ConnectionString* argument de la [ouvrir](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode ; Toutefois, en spécifiant un fournisseur dans plusieurs emplacements lors de l’appel du **ouvrir** méthode peut avoir des résultats imprévisibles. Si aucun fournisseur n’est spécifié, la propriété par défaut est MSDASQL ([fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 Le **fournisseur** propriété est en lecture/écriture lorsque la connexion est fermée et en lecture seule lorsqu’il est ouvert. Le paramètre ne prend pas effet tant que vous ouvrez le **connexion** objet ou l’accès le [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection de la **connexion** objet. Si le paramètre n’est pas valide, une erreur se produit.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de connexion (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur et un exemple de propriétés DefaultDatabase (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Fournisseur et un exemple de propriétés DefaultDatabase (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Fournisseur Microsoft OLE DB pour ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Annexe a : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)

