---
description: SQL, propriété
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d5c87c5374a0e631b08d355e5f1fc0d7c0862d23
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767408"
---
# <a name="sql-property"></a>SQL, propriété
Indique la chaîne de requête utilisée pour récupérer le [jeu d’enregistrements](../ado-api/recordset-object-ado.md).  
  
 Vous pouvez définir la propriété **SQL** au moment du design dans le [RDS. ](./datacontrol-object-rds.md) Les balises d’objet de l’objet DataControl, ou au moment de l’exécution dans le code de script.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Paramètres  
 *QueryString*  
 Valeur de **chaîne** qui contient une demande de données SQL valide.  
  
 *DataControl*  
 Variable objet qui représente un objet **RDS. DataControl** .  
  
## <a name="remarks"></a>Notes  
 En général, il s’agit d’une instruction SQL (à l’aide du dialecte du serveur de base de données), telle que `"Select * from NewTitles"` . Pour vous assurer que les enregistrements sont mis en correspondance et mis à jour correctement, une requête pouvant être mise à jour doit contenir un champ autre qu’un champ binaire long ou un champ calculé.  
  
 La propriété **SQL** est facultative si un objet métier côté serveur personnalisé récupère les données du client.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL, exemple de propriété (VBScript)](./sql-property-example-vbscript.md)   
 [Connect, propriété (RDS)](./connect-property-rds.md)   
 [Query, méthode (RDS)](./query-method-rds.md)   
 [Refresh, méthode (RDS)](./refresh-method-rds.md)   
 [SubmitChanges, méthode (RDS)](./submitchanges-method-rds.md)