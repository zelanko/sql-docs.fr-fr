---
title: Execute, méthode (objet Connection ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a52ca419f3f06e4156c278cb0ba8999c24e09ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63071135"
---
# <a name="execute-method-ado-connection"></a>Execute, méthode (objet Connection ADO)
Exécute la requête spécifiée, l’instruction SQL, le procédure stockée ou texte propre au fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un [objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) référence d’objet.  
  
#### <a name="parameters"></a>Paramètres  
 *CommandText*  
 Un **chaîne** valeur qui contient l’instruction SQL, procédure stockée, une URL ou texte propre au fournisseur à exécuter. **Si vous le souhaitez**, les noms de table peuvent être utilisés, mais uniquement si le fournisseur est SQL prenant en charge. Par exemple, si un nom de table de « Customers » est utilisés, ADO ajoute automatiquement la syntaxe SQL Select standard pour former et de passer de « SELECT * FROM Customers » en tant qu’un [!INCLUDE[tsql](../../../includes/tsql-md.md)] instruction au fournisseur.  
  
 *RecordsAffected*  
 Facultatif. Un **Long** variable sur laquelle le fournisseur retourne le nombre d’enregistrements affectée de l’opération.  
  
 *Options*  
 Facultatif. Un **Long** valeur qui indique la manière dont le fournisseur doit évaluer l’argument CommandText. Peut être un masque de bits d’une ou plusieurs [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) ou [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valeurs.  
  
 **Remarque** utilisation le **ExecuteOptionEnum** valeur **adExecuteStream** pour améliorer les performances en réduisant le traitement interne et pour les applications que vous portez à partir de Visual Basic 6.0.  
  
 N’utilisez pas **adExecuteStream** avec la **Execute** méthode d’un **connexion** objet.  
  
 N’utilisez pas les valeurs CommandTypeEnum adCmdFile ou adCmdTableDirect avec Execute. Ces valeurs peuvent uniquement être utilisées en tant qu’options avec les [méthode Open (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) et [méthode Requery](../../../ado/reference/ado-api/requery-method.md) méthodes d’un **Recordset**.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **Execute** méthode sur un [objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) objet exécute toute requête que vous passez à la méthode dans l’argument CommandText sur la connexion spécifiée. Si l’argument CommandText spécifie une requête retourne des lignes, tous les résultats générés par cette exécution sont stockés dans une nouvelle **Recordset** objet. Si la commande ne vise pas à retourner des résultats (par exemple, une requête SQL UPDATE) le fournisseur retourne **rien** aussi longtemps que l’option **adExecuteStream** est spécifié ; sinon exécutez retourne un fermé **Recordset**.  
  
 Retourné **Recordset** objet est toujours un curseur en lecture seule, avant uniquement. Si vous avez besoin d’un **Recordset** objet avec davantage de fonctionnalités, commencez par créer un **Recordset** de l’objet avec les paramètres de propriété souhaitée, puis utilisez le **Recordset** l’objet[ Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode à exécuter la requête et retourner le type de curseur souhaités.  
  
 Le contenu de la *CommandText* argument sont spécifique au fournisseur et peut être une syntaxe SQL standard ou n’importe quel format de commande spécial qui prend en charge par le fournisseur.  
  
 ExecuteComplete, événement est émis lorsque cette opération se termine.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)
