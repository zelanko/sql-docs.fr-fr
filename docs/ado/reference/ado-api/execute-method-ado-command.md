---
title: Execute, méthode (commande ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::Execute
- Command15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9508b85bc73ebbec82ad7d3bea5af5148d7c674
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772708"
---
# <a name="execute-method-ado-command"></a>Execute, méthode (commande ADO)
Exécute la requête, une instruction SQL ou une procédure stockée spécifiée dans le [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) ou [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) propriété de la [objet de commande](../../../ado/reference/ado-api/command-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) référence d’objet, d’un flux, ou **rien**.  
  
#### <a name="parameters"></a>Paramètres  
 *RecordsAffected*  
 Facultatif. Un **Long** variable sur laquelle le fournisseur retourne le nombre d’enregistrements affectée de l’opération. Le *RecordsAffected* paramètre s’applique uniquement pour les requêtes d’action ou des procédures stockées. *RecordsAffected* ne retourne pas le nombre d’enregistrements retournés par une procédure stockée ou une requête qui retourne des résultats. Pour obtenir ces informations, utilisez le [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) propriété. Le **Execute** méthode ne retournera pas les informations correctes lorsqu’il est utilisé avec **adAsyncExecute**, simplement parce que lorsqu’une commande est exécutée de façon asynchrone, le nombre d’enregistrements concernés peut encore être inconnue au moment de que la méthode est retournée.  
  
 *Paramètres*  
 Facultatif. Un **Variant** tableau de valeurs de paramètre utilisées conjointement avec la chaîne d’entrée ou le flux spécifié dans **CommandText** ou **CommandStream**. (Les paramètres de sortie ne retournent pas de valeurs correctes quand il est passé dans cet argument.)  
  
 *Options*  
 Facultatif. Un **Long** valeur qui indique la manière dont le fournisseur doit évaluer le [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) ou [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) propriété de la [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Peut être une valeur de masque de bits à l’aide de [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) et/ou [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valeurs. Par exemple, vous pouvez utiliser **adCmdText** et **adExecuteStream** en combinaison, si vous souhaitez demander à ADO d’évaluer la valeur de la **CommandText** propriété sous forme de texte, et Indique que la commande doit ignorer et ne retourne pas tous les enregistrements qui peuvent être générés lorsque le texte de commande s’exécute.  
  
> [!NOTE]
>  Utilisez le **ExecuteOptionEnum** valeur **adExecuteStream** pour améliorer les performances en réduisant le traitement interne. Si **adExecuteStream** a été spécifié, les options **adAsyncFetch** et **adAsynchFetchNonBlocking** sont ignorés. N’utilisez pas le **CommandTypeEnum** les valeurs de **adCmdFile** ou **adCmdTableDirect** avec **Execute**. Ces valeurs peuvent uniquement être utilisées en tant qu’options avec les [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) et [Requery](../../../ado/reference/ado-api/requery-method.md) méthodes d’un **Recordset**.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **Execute** méthode sur un **commande** objet exécute la requête spécifiée dans le **CommandText** propriété ou **CommandStream** propriété de l’objet.  
  
 Résultats sont retournés dans un **Recordset** (par défaut) ou en tant que flux d’informations binaires. Pour obtenir un flux binaire, spécifiez **adExecuteStream** dans *Options*, puis fournir un flux de données en définissant **Command.Properties (« sortie Stream »)**. ADO **Stream** objet peut être spécifié pour recevoir les résultats, ou un autre objet de flux tels que l’objet de réponse de IIS peut être spécifié. Si aucun flux n’a été spécifié avant d’appeler **Execute** avec **adExecuteStream**, une erreur se produit. La position du flux de données lors du retour de **Execute** est fournisseur spécifique.  
  
 Si la commande ne vise pas à retourner des résultats (par exemple, une requête SQL UPDATE) le fournisseur retourne **rien** aussi longtemps que l’option **adExecuteStream** est spécifié ; sinon exécutez retourne un fermé **Recordset**. Certains langages d’application vous permettent d’ignorer cette valeur de retour si aucun **Recordset** est souhaitée.  
  
 **Exécutez** génère une erreur si l’utilisateur spécifie une valeur pour **CommandStream** lorsque le **CommandType** est **valeur adCmdStoredProc**,  **adCmdTable**, ou **adCmdTableDirect**.  
  
 Si la requête possède des paramètres, les valeurs en cours pour le **commande** les paramètres de l’objet sont utilisées, sauf si vous remplacez par les valeurs de paramètre passées avec le **Execute** appeler. Vous pouvez remplacer un sous-ensemble des paramètres en omettant les nouvelles valeurs pour certains des paramètres lors de l’appel le **Execute** (méthode). L’ordre dans lequel vous spécifiez les paramètres est le même ordre que celui dans lequel la méthode les passe. Par exemple, si les paramètres de quatre (ou plus) et que vous souhaitez passer de nouvelles valeurs uniquement pour les première et quatrième paramètres, vous transmettriez `Array(var1,,,var4)` en tant que le *paramètres* argument.  
  
> [!NOTE]
>  Paramètres de sortie ne retournent pas de valeurs correctes quand il est passé dans le *paramètres* argument.  
  
 Un [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) événement est émis lorsque cette opération se termine.  
  
> [!NOTE]
>  Lors de l’émission de commandes contenant l’URL, ceux qui utilisent le modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, Requery et Clear, exemple de méthodes (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery et Clear, exemple de méthodes (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery et Clear, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandStream, propriété (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Execute, méthode (objet Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [ExecuteComplete, événement (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)
