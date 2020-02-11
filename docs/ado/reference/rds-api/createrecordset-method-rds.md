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
ms.openlocfilehash: 3c65f7d415864b169b683e0c9ab858506d31783b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964516"
---
# <a name="createrecordset-method-rds"></a>CreateRecordset, méthode (RDS)
Crée un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md)vide et déconnecté.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Object*  
 Variable objet qui représente un objet [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) ou [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *ColumnsInfos*  
 Tableau **Variant** d’attributs qui définit chaque colonne de l’ensemble d' **enregistrements** créé. Chaque définition de colonne contient un tableau de quatre attributs requis et un attribut facultatif.  
  
|Attribut|Description|  
|---------------|-----------------|  
|Name|Nom de l’en-tête de colonne.|  
|Type|Entier du type de données.|  
|Size|Entier de la largeur en caractères, quel que soit le type de données.|  
|Possibilité de valeurs nulles|Valeur booléenne.|  
|Scale (facultatif)|Cet attribut facultatif définit l’échelle pour les champs numériques. Si cette valeur n’est pas spécifiée, les valeurs numériques sont tronquées à une échelle de trois. La précision n’est pas affectée, mais le nombre de chiffres après la virgule décimale est tronqué à trois.|  
  
 Le jeu de tableaux de colonnes est ensuite regroupé dans un tableau, qui définit l’ensemble d' **enregistrements**.  
  
## <a name="remarks"></a>Notes  
 L’objet métier côté serveur peut remplir le **jeu d’enregistrements** résultant avec les données d’un fournisseur de données non-OLE DB, tel qu’un fichier de système d’exploitation contenant des cotations boursières.  
  
 Le tableau suivant répertorie les valeurs [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) prises en charge par la méthode **CreateRecordset** . Le nombre indiqué est le numéro de référence utilisé pour définir des champs.  
  
 Chacun des types de données est de longueur fixe ou de longueur variable. Les types de longueur fixe doivent être définis avec une taille de-1, car la taille est prédéterminée et une définition de taille est toujours requise. Les types de données de longueur variable autorisent une taille comprise entre 1 et 32767.  
  
 Pour certains types de données de variable, le type peut être forcé au type noté dans la colonne de substitution. Vous ne verrez pas les substitutions tant que le **jeu d’enregistrements** n’a pas été créé et rempli. Vous pouvez ensuite vérifier le type de données réel, si nécessaire.  
  
|Longueur|Constant|Number|Substitution|  
|------------|--------------|------------|------------------|  
|Résolution|**adTinyInt**|16||  
|Résolution|**adSmallInt**|2||  
|Résolution|**adInteger**|3||  
|Résolution|**adBigInt**|20||  
|Résolution|**adUnsignedTinyInt**|17||  
|Résolution|**adUnsignedSmallInt**|18||  
|Résolution|**adUnsignedInt**|19||  
|Résolution|**adUnsignedBigInt**|21||  
|Résolution|**adSingle**|4||  
|Résolution|**adDouble**|5||  
|Résolution|**adCurrency**|6||  
|Résolution|**adDecimal**|14||  
|Résolution|**adNumeric**|131||  
|Résolution|**adBoolean**|11||  
|Résolution|**adError**|10||  
|Résolution|**adGuid**|72||  
|Résolution|**adDate**|7||  
|Résolution|**adDBDate**|133||  
|Résolution|**adDBTime**|134||  
|Résolution|**adDBTimestamp**|135|7|  
|Variable|**adBSTR**|8|130|  
|Variable|**adChar**|129|200|  
|Variable|**Varchar**|200||  
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
 [CreateRecordset, exemple de méthode (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [CreateRecordset, exemple de méthode (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [CreateObject, méthode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



