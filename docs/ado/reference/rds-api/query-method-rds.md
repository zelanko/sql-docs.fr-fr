---
title: Query, méthode (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
author: rothja
ms.author: jroth
ms.openlocfilehash: b3025f37b47cd545e7e7cde127e96740077ab961
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751496"
---
# <a name="query-method-rds"></a>Query, méthode (RDS)
Utilise une chaîne de requête SQL valide pour retourner un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Recordset*  
 Variable objet qui représente un objet **Recordset** .  
  
 *DataFactory*  
 Variable objet qui représente un objet [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) .  
  
 *Connection*  
 Valeur de **chaîne** qui contient les informations de connexion au serveur. Cela est similaire à la propriété [Connect](../../../ado/reference/rds-api/connect-property-rds.md) .  
  
 *Requête*  
 **Chaîne** qui contient la requête SQL.  
  
## <a name="remarks"></a>Remarques  
 La requête doit utiliser le dialecte SQL du serveur de base de données. Un état de résultat est retourné en cas d’erreur avec la requête qui a été exécutée. La méthode de **requête** n’effectue aucune vérification de la syntaxe sur la chaîne de **requête** .  
  
## <a name="applies-to"></a>S'applique à  
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataFactory (exemple d’objet), Query (exemple de méthode) et CreateObject (exemple de méthode) (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


