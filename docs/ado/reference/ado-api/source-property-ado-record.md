---
description: Source, propriété (objet Record ADO)
title: Source, propriété (ADO record) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e755fb4a34e170efea760428021b540a182156c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777408"
---
# <a name="source-property-ado-record"></a>Source, propriété (objet Record ADO)
Indique la source de données ou l’objet représenté par l' [enregistrement](./record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type Variant** qui indique l’entité représentée par l' **enregistrement**.  
  
## <a name="remarks"></a>Notes  
 La propriété **source** retourne l’argument *source* de la méthode d' [ouverture](./open-method-ado-record.md) de l’objet **Record** . Elle peut contenir une chaîne d’URL absolue ou relative. Une URL absolue peut être utilisée sans définir la propriété [ActiveConnection](./activeconnection-property-ado.md) pour ouvrir directement l’objet **Record** . Dans ce cas, un objet de **connexion** implicite est créé.  
  
 La propriété **source** peut également contenir une référence à un **Recordset**déjà ouvert, ce qui ouvre un objet **Record** représentant la ligne actuelle dans le **Recordset**.  
  
 La propriété **source** peut également contenir une référence à un objet de [commande](./command-object-ado.md) qui retourne une ligne unique de données du fournisseur.  
  
 Si la propriété **ActiveConnection** est également définie, la propriété **source** doit pointer vers un objet qui existe dans l’étendue de cette connexion. Par exemple, dans les espaces de noms structurés en arborescence, si la propriété **source** contient une URL absolue, elle doit pointer vers un nœud qui existe à l’intérieur de l’étendue du nœud identifié par l’URL dans la chaîne de connexion. Si la propriété **source** contient une URL relative, elle est validée dans le contexte défini par la propriété **ActiveConnection** .  
  
 La propriété **source** est en lecture/écriture lorsque l’objet **enregistrement** est fermé, et est en lecture seule lorsque l’objet **enregistrement** est ouvert.  
  
> [!NOTE]
>  Les URL utilisant le schéma http appellera automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](./record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Source, propriété (erreur ADO)](./source-property-ado-error.md)   
 [Source, propriété (objet Recordset ADO)](./source-property-ado-recordset.md)