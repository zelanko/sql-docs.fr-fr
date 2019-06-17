---
title: Utilisation d’ADO pour la publication Internet | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ac7922dda2d486f4783d1230296dc89b81cb4fe3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718610"
---
# <a name="using-ado-for-internet-publishing"></a>Utilisation d’ADO pour la publication Internet
[Le fournisseur OLE DB pour la publication Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) montre un exemple spécifique de l’accès aux données hétérogènes avec ADO. Même si les exemples de cette section sont spécifiques à l’aide du fournisseur de publication Internet, les principes illustrés doivent être similaires lors de l’utilisation d’ADO avec d’autres fournisseurs de données hétérogènes, tel qu’un fournisseur à un magasin de courrier électronique.  
  
## <a name="urls"></a>URL  
 Uniform Resource Locator (URL) peut être utilisé comme alternative à des chaînes de connexion et le texte de la commande pour spécifier les sources de données et l’emplacement des fichiers et répertoires. Vous pouvez utiliser des URL avec le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) et **Recordset** objets et avec le **enregistrement** et **Stream** objets.  
  
 Pour plus d’informations sur l’utilisation des URL, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Champs d’enregistrement  
 La différence qui distingue les données hétérogènes des données homogènes est que dans le premier cas, chaque ligne de données, ou **enregistrement**, peut avoir un autre ensemble de colonnes, ou **champs**. Pour les données homogènes, chaque ligne a le même ensemble de colonnes. Pour plus d’informations sur les champs spécifiques au fournisseur de publication Internet, consultez [enregistrements et champs supplémentaires spécifiques au fournisseur](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Ajout de nouveaux champs  
 Plusieurs objets ADO ont été améliorées pour fonctionner conjointement avec **enregistrement** et **Stream** objets.  
  
-   Le [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection [Append](../../../ado/reference/ado-api/append-method-ado.md) (méthode), qui crée et ajoute un [champ](../../../ado/reference/ado-api/field-object.md) de l’objet à la collection, peuvent également spécifier la valeur de la **champ**.  
  
-   Le [mise à jour](../../../ado/reference/ado-api/update-method.md) méthode finalise l’ajout ou la suppression de champs à la collection.  
  
-   En tant que raccourci et alternative à la **Append** (méthode), vous pouvez créer des champs en affectant une valeur à un champ non défini ou précédemment supprimé.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Fournisseur OLE DB pour la publication Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Enregistrements et champs fournis par le fournisseur](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrement objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Historique d’ADO](../../../ado/guide/ado-history.md)
