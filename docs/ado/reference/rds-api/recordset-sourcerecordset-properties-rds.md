---
title: Jeu d’enregistrements, SourceRecordset, propriétés (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3ec8dbdce6a813663f7909adb2a9ec1edacee9b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718763"
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Recordset et SourceRecordset, propriétés (RDS)
Indique le **Recordset** objet retourné à partir d’un objet métier personnalisé.  
  
 **S’applique à :** [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataControl*  
 Une variable objet qui représente un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 *Recordset*  
 Une variable objet qui représente un **Recordset** objet.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez définir le **SourceRecordset** propriété à un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) retourné à partir d’un objet métier personnalisé.  
  
 Ces propriétés permettent à une application gérer le processus de liaison au moyen d’un processus personnalisé. Ils reçoivent un ensemble de lignes encapsulée dans un **Recordset** afin que vous pouvez interagir directement avec le **Recordset**, effectuer des actions telles que la définition des propriétés ou l’itération via la **Recordset** .  
  
 Vous pouvez définir le **SourceRecordset** propriété ou lecture la **Recordset** propriété au moment de l’exécution dans le code de script.  
  
 **SourceRecordset** est une propriété en écriture seule, contrairement à la **Recordset** propriété, qui est une propriété en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset et SourceRecordset, propriétés-exemple (VBScript)](../../../ado/reference/rds-api/recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [CreateRecordset, méthode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Query, méthode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)


