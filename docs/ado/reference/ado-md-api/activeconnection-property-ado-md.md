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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911593"
---
# <a name="activeconnection-property-ado-md"></a>ActiveConnection, propriété (ADO MD)
Indique à quel objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ADO appartient actuellement le catalogue ou l’CellSet actuel.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type Variant** qui contient une chaîne définissant une connexion ou un objet de **connexion** . La valeur par défaut est vide.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez définir cette propriété sur un objet de **connexion** ADO valide ou une chaîne de connexion valide. Quand cette propriété est définie sur une chaîne de connexion, le fournisseur crée un objet de **connexion** à l’aide de cette définition et ouvre la connexion.  
  
 Si vous utilisez l’argument *ActiveConnection* de la méthode [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) pour ouvrir un objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) , la propriété **ActiveConnection** héritera de la valeur de l’argument.  
  
 L’affectation de la valeur **Nothing** à la propriété **ActiveConnection** d’un objet [catalogue](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) libère les données associées, y compris les données de la collection [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) et les objets [dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [hiérarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md)et [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) associés. La fermeture d’un objet de **connexion** qui a été utilisé pour ouvrir un **catalogue** a le même effet que l’affectation de la valeur **Nothing**à la propriété **ActiveConnection** .  
  
 La modification de la base de données par défaut de la connexion référencée par la propriété **ActiveConnection** d’un objet **catalogue** invalide le contenu du **catalogue**.  
  
 Une erreur se produit si vous tentez de modifier la propriété **ActiveConnection** pour un objet **Cellset** ouvert.  
  
> [!NOTE]
>  Dans Visual Basic, n’oubliez pas d’utiliser le mot clé **Set** lors de la définition de la propriété **ActiveConnection** sur un objet de **connexion** . Si vous omettez le mot clé **Set** , vous définissez en fait la propriété **ActiveConnection** comme étant égale à la propriété par défaut de l’objet de **connexion** , **ConnectionString**. Le code fonctionnera. Toutefois, vous allez créer une connexion supplémentaire à la source de données, ce qui peut avoir des répercussions négatives sur les performances.  
  
 Lorsque vous utilisez le fournisseur de données MSOLAP, définissez la source de données dans une chaîne de connexion sur un nom de serveur et définissez le catalogue initial sur le nom d’un catalogue à partir de la source de données. Pour vous connecter à un fichier de cube déconnecté d’un serveur, définissez l’emplacement sur le chemin d’accès complet au. Fichier CUB. Dans les deux cas, définissez le fournisseur sur le nom du fournisseur. Par exemple, la chaîne suivante utilise le fournisseur MSOLAP pour se connecter à un catalogue nommé Bobs Video Store sur un serveur nommé **ServerName**:  
  
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
 [CellSet, exemple (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open, méthode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
