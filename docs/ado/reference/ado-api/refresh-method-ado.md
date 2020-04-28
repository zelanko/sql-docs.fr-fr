---
title: Refresh, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a676bf5eb3d8d98f1b2eb9367aa8ad56f0da209d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931251"
---
# <a name="refresh-method-ado"></a>Refresh, méthode (ADO)
Met à jour les objets d’une collection pour refléter les objets disponibles et spécifiques au fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Notes  
 La méthode **Refresh** effectue différentes tâches en fonction de la collection à partir de laquelle vous l’appelez.  
  
### <a name="parameters"></a>Paramètres  
 L’utilisation de la méthode **Refresh** sur la collection [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) d’un objet [Command](../../../ado/reference/ado-api/command-object-ado.md) récupère les informations sur les paramètres côté fournisseur pour la procédure stockée ou la requête paramétrable spécifiée dans l’objet **Command** . La collection est vide pour les fournisseurs qui ne prennent pas en charge les appels de procédure stockée ou les requêtes paramétrables.  
  
 Vous devez définir la propriété [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) de l’objet de **commande** sur un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) valide, la propriété [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) sur une commande valide et la propriété [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) sur **adCmdStoredProc** avant d’appeler la méthode **Refresh** .  
  
 Si vous accédez à la collection **Parameters** avant d’appeler la méthode **Refresh** , ADO appellera automatiquement la méthode et remplira la collection pour vous.  
  
> [!NOTE]
>  Si vous utilisez la méthode **Refresh** pour obtenir des informations sur les paramètres du fournisseur et qu’elle retourne un ou plusieurs objets de [paramètre](../../../ado/reference/ado-api/parameter-object.md) de type de données de longueur variable, ADO peut allouer de la mémoire pour les paramètres en fonction de leur taille maximale potentielle, ce qui entraîne une erreur pendant l’exécution. Vous devez définir explicitement la propriété [Size](../../../ado/reference/ado-api/size-property-ado-parameter.md) pour ces paramètres avant d’appeler la méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) pour éviter les erreurs.  
  
### <a name="fields"></a>Champs  
 L’utilisation de la méthode **Refresh** sur la collection [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) n’a aucun effet visible. Pour récupérer les modifications de la structure de base de données sous-jacente, vous devez utiliser la méthode [Requery](../../../ado/reference/ado-api/requery-method.md) ou, si l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ne prend pas en charge les signets, la méthode [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) .  
  
### <a name="properties"></a>Propriétés  
 L’utilisation de la méthode **Refresh** sur une collection **Properties** de certains objets remplit la collection avec les propriétés dynamiques exposées par le fournisseur. Ces propriétés fournissent des informations sur les fonctionnalités spécifiques au fournisseur, au-delà des propriétés intégrées prises en charge par ADO.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Axes, collection](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Collection Columns](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs, collection](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions, collection](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Collection d’erreurs](../../../ado/reference/ado-api/errors-collection-ado.md)|[Collection Fields](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Collection de groupes](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hiérarchies, collection](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexer la collection](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Collection Keys](../../../ado/reference/adox-api/keys-collection-adox.md)|[Collection de niveaux](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Collection Members](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Collection Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Collection de positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures, collection](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Collection Properties](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables, collection](../../../ado/reference/adox-api/tables-collection-adox.md)|[Collection d’utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views, collection](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Voir aussi  
 [Refresh, exemple de méthode (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Refresh, exemple de méthode (VC + +)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Count, propriété (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)
