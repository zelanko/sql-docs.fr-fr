---
title: Propriété SQL | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b3222c39515bad505d24b10e31b36a9c1c61965
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604469"
---
# <a name="sql-property"></a>SQL, propriété
Indique la chaîne de requête utilisée pour récupérer le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Vous pouvez définir le **SQL** propriété au moment du design dans le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) balises d’objet de l’objet, ou en cours d’exécution dans le code de script.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Chaîne de requête*  
 Un **chaîne** valeur qui contient une demande de données SQL valide.  
  
 *DataControl*  
 Une variable objet qui représente un **RDS. DataControl** objet.  
  
## <a name="remarks"></a>Notes  
 En règle générale, il s’agit d’une instruction de SQL (à l’aide du dialecte du serveur de base de données), tel que `"Select * from NewTitles"`. Pour vous assurer que les enregistrements sont mis en correspondance et mis à jour avec précision, une requête actualisable doit contenir un champ autre qu’un champ binaire longue ou un champ calculé.  
  
 Le **SQL** propriété est facultative si un objet métier côté serveur personnalisé récupère les données pour le client.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété SQL (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Se connecter, propriété (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Query, méthode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges, méthode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


