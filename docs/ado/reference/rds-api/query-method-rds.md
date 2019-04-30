---
title: Méthode (RDS) de requête | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a64a4f1a51d678e70516f277c08071f5884492c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225840"
---
# <a name="query-method-rds"></a>Query, méthode (RDS)
Utilise une chaîne de requête SQL valide pour retourner un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Recordset*  
 Une variable objet qui représente un **Recordset** objet.  
  
 *DataFactory*  
 Une variable objet qui représente un [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet.  
  
 *Connexion*  
 Un **chaîne** valeur qui contient les informations de connexion du serveur. Ceci est similaire à la [Connect](../../../ado/reference/rds-api/connect-property-rds.md) propriété.  
  
 *Requête*  
 Un **chaîne** qui contient la requête SQL.  
  
## <a name="remarks"></a>Notes  
 La requête doit utiliser le dialecte SQL du serveur de base de données. Un état de résultat est retourné s’il existe une erreur avec la requête a été exécutée. Le **requête** méthode n’effectue pas de toute vérification syntaxique de le **requête** chaîne.  
  
## <a name="applies-to"></a>S'applique à  
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataFactory (exemple d’objet), Query (exemple de méthode) et CreateObject (exemple de méthode) (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


