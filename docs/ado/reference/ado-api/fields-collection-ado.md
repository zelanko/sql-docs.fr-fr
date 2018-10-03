---
title: Fields, Collection (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74e6deb0caba88e6bbcf2897dcfa4aaaa22f04d0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762597"
---
# <a name="fields-collection-ado"></a>Fields, collection (ADO)
Contient tous les [champ](../../../ado/reference/ado-api/field-object.md) objets d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ou [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet.  
  
## <a name="remarks"></a>Notes  
 Un **Recordset** objet possède un **champs** collection composée de **champ** objets. Chaque **champ** objet correspond à une colonne dans la **Recordset**. Vous pouvez remplir le **champs** collection avant d’ouvrir le **Recordset** en appelant le [Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md) méthode sur la collection.  
  
> [!NOTE]
>  Consultez le **champ** rubrique d’objet pour une explication plus détaillée de l’utilisation de **champ** objets.  
  
 Le **champs** collection a un [Append](../../../ado/reference/ado-api/append-method-ado.md) (méthode), qui crée et ajoute provisoirement un **champ** objet à la collection et un **mettre à jour**(méthode), qui finalise les ajouts et les suppressions.  
  
 Un **enregistrement** objet comporte deux champs spéciaux qui peuvent être indexées avec [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) constantes. Une seule constante accède à un champ contenant le flux par défaut pour le **enregistrement**, et l’autre accède à un champ contenant la chaîne d’URL absolue pour le **enregistrement**.  
  
 Certains fournisseurs (par exemple, le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) peut remplir le **champs** collection avec un sous-ensemble des champs disponibles pour le **enregistrement** ou **Recordset**. Autres champs ne seront pas ajoutés à la collection jusqu'à ce qu’ils sont tout d’abord référencés par nom ou indexés par votre code.  
  
 Si vous essayez de référencer un champ inexistant par son nom, un nouveau **champ** objet sera ajouté à la **champs** collection avec un [état](../../../ado/reference/ado-api/status-property-ado-field.md) de  **adFieldPendingInsert**. Lorsque vous appelez [mise à jour](../../../ado/reference/ado-api/update-method.md), ADO crée un nouveau champ dans votre source de données si autorisé par votre fournisseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de Collection de champs, méthodes et événements](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)
