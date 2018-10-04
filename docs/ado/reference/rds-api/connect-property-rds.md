---
title: Se connecter, propriété (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: abf2b751f6f1e89cf51560ad7e0d38aa05da7b8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851469"
---
# <a name="connect-property-rds"></a>Connect, propriété (RDS)
Indique le nom de la base de données à partir de laquelle les opérations de requête et de mise à jour sont exécutées.  
  
 Vous pouvez définir le **Connect** propriété au moment du design dans le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) balises d’objet de l’objet, ou en cours d’exécution dans le code (par exemple, VBScript) de script.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectionString*  
 Une chaîne de connexion valide. Pour plus d’informations sur les chaînes de connexion, consultez le [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété ou la documentation du fournisseur.  
  
> [!NOTE]
>  Spécification MS Remote comme le fournisseur pour le **RDS. DataControl** créerait un scénario à quatre niveaux. Scénarios supérieures à trois niveaux n’ont pas été testés et ne doivent pas être nécessaire.  
  
 *DataControl*  
 Une variable objet qui représente un **RDS. DataControl** objet.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Connect, exemple (VBScript)](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Query, méthode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh, méthode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges, méthode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


