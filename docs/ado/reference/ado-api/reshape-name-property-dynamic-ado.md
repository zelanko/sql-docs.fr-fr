---
title: Reshape Name, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a07ec878b1198fbf23bfb251460d83869313c83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696828"
---
# <a name="reshape-name-property-dynamic-ado"></a>Reshape Name, propriété dynamique (ADO)
Spécifie un nom pour le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **chaîne** valeur représentant le nom de la **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Les noms persistent pendant la durée de la connexion ou jusqu'à ce que le **Recordset** est fermé.  
  
 Le **Reshape Name** propriété est principalement destinée à utiliser avec la fonctionnalité de remise en forme de la [Microsoft Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) fournisseur de services. Noms doivent être uniques pour participer à la remise en forme.  
  
 Cette propriété est en lecture seule, mais peut être définie lorsque indirectement un **Recordset** est créé. Par exemple, si une clause d’une commande Shape crée un **Recordset** et lui donne un nom d’alias à l’aide de la **AS** mot clé, l’alias est affecté à la **Reshape Name** propriété. Si aucun alias n’est déclaré, le **Reshape Name** un nom unique généré par le service de mise en forme des données est affectée à la propriété. Si le nom d’alias est le même que le nom d’un existant **Recordset**, ni **Recordset** puissent être REFORMÉES jusqu'à ce qu’un d’eux est libéré. Le comportement par défaut peut être modifié en définissant un nom unique le [Reshape Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) propriété sur une connexion ADO **True**. Définition de cette propriété donne les données de mise en forme de service l’autorisation de modifier le nom d’utilisateur affecté, si nécessaire, pour garantir l’unicité. Pour plus d’informations sur la mise en forme, consultez [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Utilisez le **Reshape Name** propriété lorsque vous souhaitez faire référence à un **Recordset** dans une commande de forme, ou lorsque vous ne connaissez pas le nom, car il a été généré par le Service de mise en forme des données. Dans ce cas, vous pourrez générer une commande SHAPE en concaténant la commande autour de la chaîne retournée par la **Reshape Name** propriété.  
  
 **Remodeler nom** est une propriété dynamique ajoutée à la **Recordset** l’objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [En général, les commandes de forme](../../../ado/guide/data/shape-commands-in-general.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
