---
title: ActiveConnection, propriété (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae0b32385b98ac1b48688a7f89bbd7c91842a106
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67911593"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection, propriété (ADO MD)
Indique à quel ADO [connexion](../../../ado/reference/ado-api/connection-object-ado.md) l’ensemble de cellules en cours de l’objet ou le catalogue auquel appartient actuellement.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Variant** qui contient une chaîne définissant une connexion ou **connexion** objet. La valeur par défaut est vide.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez définir cette propriété sur une ADO valide **connexion** objet ou une chaîne de connexion valide. Lorsque cette propriété est définie à une chaîne de connexion, le fournisseur crée un **connexion** de l’objet à l’aide de cette définition et ouvre la connexion.  
  
 Si vous utilisez le *ActiveConnection* argument de la [ouvrir](../../../ado/reference/ado-md-api/open-method-ado-md.md) méthode pour ouvrir un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet, le **ActiveConnection** propriété dont la valeur hériter de la valeur de l’argument.  
  
 Définissant le **ActiveConnection** propriété d’un [catalogue](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) objet **rien** libère les données associées, y compris les données dans le [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) collection et toutes liées [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [hiérarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md), et [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets. Fermer un **connexion** objet qui a été utilisé pour ouvrir un **catalogue** a le même effet en tant que paramètre le **ActiveConnection** propriété **rien**.  
  
 Modification de la base de données par défaut de la connexion référencée par le **ActiveConnection** propriété d’un **catalogue** objet invalide le contenu de la **catalogue**.  
  
 Une erreur se produit si vous tentez de modifier le **ActiveConnection** propriété d’une connexion **Cellset** objet.  
  
> [!NOTE]
>  En Visual Basic, pensez à utiliser le **définir** mot clé lors de la définition la **ActiveConnection** propriété à un **connexion** objet. Si vous omettez le **définir** mot clé, vous serez réellement être défini le **ActiveConnection** propriété égale à la **connexion** propriété par défaut de l’objet,  **ConnectionString**. Le code fonctionne ; Toutefois, vous allez créer une connexion supplémentaire à la source de données, qui peut avoir des implications de performances.  
  
 Lorsque vous utilisez le fournisseur de données MSOLAP, affectez la source de données dans une chaîne de connexion à un nom de serveur et catalogue initial pour le nom d’un catalogue de la source de données. Pour vous connecter à un fichier de cube est déconnecté d’un serveur, définissez l’emplacement sur le chemin d’accès complet à la. Fichier de cube. Dans les deux cas, définir le fournisseur sur le nom du fournisseur. Par exemple, la chaîne suivante utilise le fournisseur MSOLAP pour se connecter à un catalogue nommé Bobs vidéo Store sur un serveur nommé **nom_serveur**:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 La chaîne suivante se connecte à un fichier de cube local à l’emplacement C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub :  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Catalog, objet (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec Cellset (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open, méthode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
