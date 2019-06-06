---
title: NextRecordset, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 33cc979e0a3af9b684899cf7563573fd6ac8dadd
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707281"
---
# <a name="nextrecordset-method-ado"></a>NextRecordset, méthode (ADO)
Efface actuel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) de l’objet et renvoie la prochaine **Recordset** en exécutant une série de commandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Recordset** objet. Dans le modèle de syntaxe, *recordset1* et *recordset2* peut être le même **Recordset** objet, ou vous pouvez utiliser des objets distincts. Lors de l’utilisation de distinct **Recordset** objets, réinitialiser le **ActiveConnection** propriété sur l’original **Recordset** (*recordset1*) une fois **NextRecordset** a été appelée va générer une erreur.  
  
#### <a name="parameters"></a>Paramètres  
 *RecordsAffected*  
 Facultatif. Un **Long** variable sur laquelle le fournisseur retourne le nombre d’enregistrements affectée de l’opération en cours.  
  
> [!NOTE]
>  Ce paramètre retourne uniquement le nombre d’enregistrements affectés par une opération ; elle ne retourne pas le nombre d’enregistrements à partir d’une instruction select utilisée pour générer le **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **NextRecordset** méthode pour retourner les résultats de la commande suivante dans une instruction composée de commande ou d’une procédure stockée qui retourne plusieurs résultats. Si vous ouvrez un **Recordset** objet basé sur une instruction composée de commande (par exemple, « sélectionnez \* à partir de table1 ; Sélectionnez \* à partir de table2 ») à l’aide de la [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) méthode sur un [commande](../../../ado/reference/ado-api/command-object-ado.md) ou le [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode sur un **Recordset**, ADO exécute uniquement la première commande et retourne les résultats à *recordset*. Pour accéder aux résultats des commandes suivantes dans l’instruction, appelez le **NextRecordset** (méthode).  
  
 Tant que des résultats supplémentaires et la **Recordset** contenant les instructions composées n’est pas déconnectée ou marshalée au-delà des limites de processus, le **NextRecordset** méthode continuera à retourner **Recordset** objets. Si une commande retourne des lignes s’exécute correctement mais ne renvoie aucun enregistrement, retourné **Recordset** objet sera ouvert mais vide. Test pour ce cas en vous assurant que le [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) et [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriétés sont toutes deux **True**. Si une commande sans renvoi à la ligne s’exécute correctement, retourné **Recordset** objet va être fermé, vous pouvez vérifier en testant la [état](../../../ado/reference/ado-api/state-property-ado.md) propriété sur le **Recordset**. Lorsqu’il n’y a plus aucun résultat, *recordset* sera défini sur *rien*.  
  
 Le **NextRecordset** méthode n’est pas disponible sur un déconnecté **Recordset** objet, où [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) a été défini sur **rien**(dans Microsoft Visual Basic) ou NULL (dans d’autres langages).  
  
 Si une modification est en cours d’exécution en mode de mise à jour immédiate, l’appel la **NextRecordset** méthode génère une erreur ; appelez le [mettre à jour](../../../ado/reference/ado-api/update-method.md) ou [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) méthode première.  
  
 Pour passer des paramètres pour plusieurs commandes dans l’instruction composée en remplissant la [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection, ou en passant un tableau avec l’original **Open** ou **Execute** appel, les paramètres doivent être dans le même ordre dans la collection ou un tableau en tant que leurs commandes correspondantes dans la série de commandes. Vous devez terminer la lecture de tous les résultats avant de lire les valeurs de paramètre de sortie.  
  
 Votre fournisseur OLE DB détermine quand chaque commande dans une instruction composée est exécutée. Le [fournisseur Microsoft OLE DB pour SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), par exemple, s’exécute toutes les commandes dans un lot lorsqu’il reçoit l’instruction composée. Résultant **Recordsets** sont simplement retournés lorsque vous appelez **NextRecordset**.  
  
 Toutefois, les autres fournisseurs peuvent exécuter la commande suivante dans une instruction uniquement après l’appel de NextRecordset. Pour ces fournisseurs, si vous fermez explicitement le **Recordset** avant d’exécuter l’instruction de la commande entière, par l’objet ADO s’exécute jamais les commandes restantes.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode NextRecordset, exemple (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [NextRecordset, exemple de méthode (VC++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
