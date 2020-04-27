---
title: Propriété Remodel Name-Dynamic (ADO) | Microsoft Docs
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
ms.openlocfilehash: ec72b2b1908f967caee4610e27315acaab787ac9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917174"
---
# <a name="reshape-name-property-dynamic-ado"></a>Reshape Name, propriété dynamique (ADO)
Spécifie un nom pour l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur de **chaîne** qui est le nom de l’ensemble d' **enregistrements**.  
  
## <a name="remarks"></a>Notes  
 Les noms sont conservés pendant la durée de la connexion ou jusqu’à la fermeture du **Recordset** .  
  
 La propriété **Remodel Name** est principalement destinée à être utilisée avec la nouvelle fonctionnalité de mise en forme de [Microsoft Data shaping service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) fournisseur de services. Les noms doivent être uniques pour participer à la remise en forme.  
  
 Cette propriété est en lecture seule, mais peut être définie indirectement lors de la création d’un **jeu d’enregistrements** . Par exemple, si une clause d’une commande SHAPE crée un **Recordset** et lui attribue un nom d’alias à l’aide du mot clé **As** , l’alias est affecté à la propriété **Remodel Name** . Si aucun alias n’est déclaré, la propriété **Remodel Name** reçoit un nom unique généré par le service de mise en forme des données. Si le nom d’alias est identique au nom d’un **jeu d’enregistrements**existant, aucun **jeu d’enregistrements** ne peut être remodelé tant que l’un d’eux n’est pas libéré. Le comportement par défaut peut être modifié en définissant un nom unique dans la propriété [Remodel Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) de la connexion ADO sur **true**. La définition de cette propriété donne au service de mise en forme des données la permission de modifier le nom attribué à l’utilisateur, si nécessaire, pour garantir l’unicité. Pour plus d’informations sur la mise en forme, consultez [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Utilisez la propriété **reformer le nom** lorsque vous souhaitez faire référence à un **jeu d’enregistrements** dans une commande Shape ou lorsque vous ne connaissez pas le nom, car il a été généré par le service de mise en forme des données. Dans ce cas, vous pouvez générer une commande SHAPE en concaténant la commande autour de la chaîne retournée par la propriété **Remodel Name** .  
  
 **Remodel Name** est une propriété dynamique ajoutée à la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) de l’objet **Recordset** lorsque la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) a la valeur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Mettre en forme les commandes en général](../../../ado/guide/data/shape-commands-in-general.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
