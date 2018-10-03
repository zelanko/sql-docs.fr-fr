---
title: CreateRecordset, méthode (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 791586badfeff0c1bde35b5cdf25ba750f79fe80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779027"
---
# <a name="createrecordset-method-rds"></a>CreateRecordset, méthode (RDS)
Crée un vide, déconnecté [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Objet*  
 Une variable objet qui représente un [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) ou [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *ColumnsInfos*  
 Un **Variant** tableau d’attributs qui définit chaque colonne dans le **Recordset** créé. Chaque définition de colonne contient un tableau de quatre attributs obligatoires et un attribut facultatif.  
  
|Attribute|Description|  
|---------------|-----------------|  
|Nom   |Nom de l’en-tête de colonne.|  
|Type|Entier du type de données.|  
|Taille|Entier de la largeur en caractères, quel que soit le type de données.|  
|Possibilité de valeurs nulles|Valeur booléenne.|  
|Mise à l’échelle (facultatif)|Cet attribut facultatif définit l’échelle pour les champs numériques. Si cette valeur n’est pas spécifiée, des valeurs numériques sont tronquées à une échelle de trois. Précision n’est pas affectée, mais le nombre de chiffres après la virgule décimale est tronqué à trois.|  
  
 L’ensemble de tableaux de colonnes est ensuite regroupé dans un tableau, qui définit le **Recordset**.  
  
## <a name="remarks"></a>Notes  
 L’objet métier côté serveur peut remplir résultant **Recordset** avec des données depuis un fournisseur de données non - OLE DB, comme un système d’exploitation fichiers contenant des cotations boursières.  
  
 Le tableau suivant répertorie les [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valeurs prises en charge par le **CreateRecordset** (méthode). Le nombre répertorié est le numéro de référence utilisé pour définir des champs.  
  
 Chacun des types de données est de longueur fixe ou longueur variable. Types de longueur fixe doivent être définies avec une taille de -1, car la taille est prédéterminée et définition de la taille est toujours requise. Types de données de longueur variable permettent une taille comprise entre 1 et 32767.  
  
 Pour certains types de données de variable, le type peut être forcé au type indiqué dans la colonne de Substitution. Vous ne verrez pas les substitutions qu’après le **Recordset** est créé et rempli. Vous pouvez alors vérifier pour le type de données réelles, si nécessaire.  
  
|Longueur|Constante|Number|Substitution|  
|------------|--------------|------------|------------------|  
|Fixe|**adTinyInt**|16||  
|Fixe|**adSmallInt**|2||  
|Fixe|**adInteger**|3||  
|Fixe|**adBigInt**|20||  
|Fixe|**adUnsignedTinyInt**|17||  
|Fixe|**adUnsignedSmallInt**|18||  
|Fixe|**adUnsignedInt**|19||  
|Fixe|**adUnsignedBigInt**|21||  
|Fixe|**adSingle**|4||  
|Fixe|**adDouble**|5||  
|Fixe|**adCurrency**|6||  
|Fixe|**adDecimal**|14||  
|Fixe|**adNumeric**|131||  
|Fixe|**adBoolean**|11||  
|Fixe|**adError**|10||  
|Fixe|**adGuid**|72||  
|Fixe|**adDate**|7||  
|Fixe|**adDBDate**|133||  
|Fixe|**adDBTime**|134||  
|Fixe|**adDBTimestamp**|135|7|  
|Variable|**adBSTR**|8|130|  
|Variable|**adChar**|129|200|  
|Variable|**adVarChar**|200||  
|Variable|**adLongVarChar**|201|200|  
|Variable|**adWChar**|130||  
|Variable|**adVarWChar**|202|130|  
|Variable|**adLongVarWChar**|203|130|  
|Variable|**adBinary**|128||  
|Variable|**adVarBinary**|204||  
|Variable|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode CreateRecordset, exemple (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [CreateRecordset, méthode-exemple (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [CreateObject, méthode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



