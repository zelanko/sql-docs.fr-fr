---
title: "Jeu d’enregistrements, les propriétés de SourceRecordset (RDS) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2c5ce9fc2ef297c44f4bcfb3868168d0cb1dda15
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-sourcerecordset-properties-rds"></a>Jeu d’enregistrements, les propriétés de SourceRecordset (RDS)
Indique le **Recordset** objet retourné à partir d’un objet métier personnalisé.  
  
 **S’applique à :** [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *Jeu d’enregistrements*  
 Une variable objet qui représente un **Recordset** objet.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez définir le **SourceRecordset** propriété un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) retourné à partir d’un objet métier personnalisé.  
  
 Ces propriétés permettent à une application de gérer le processus de liaison au moyen d’un processus personnalisé. Ils reçoivent un rowset inséré dans un **Recordset** afin que vous pouvez interagir directement avec le **Recordset**, effectuer des actions telles que les propriétés de paramètre ou itération au sein de la **Recordset**.  
  
 Vous pouvez définir le **SourceRecordset** propriété ou la lecture du **Recordset** propriété au moment de l’exécution dans le code de script.  
  
 **SourceRecordset** est une propriété en écriture seule, contrairement à la **Recordset** propriété, qui est une propriété en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset et SourceRecordset, propriétés-exemple (VBScript)](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [CreateRecordset, méthode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Méthode de requête (RDS)](../../../ado/reference/rds-api/query-method-rds.md)



