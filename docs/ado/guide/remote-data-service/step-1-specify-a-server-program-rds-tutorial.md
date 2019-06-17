---
title: 'Étape 1 : Spécifier un programme serveur (didacticiel RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 03d60a00a116f771e3854a4fe1b6b5ec512c0708
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704181"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Étape 1 : Spécifier un programme serveur (tutoriel RDS)
Dans la plupart des cas, utilisez le [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) méthode pour spécifier le programme de serveur par défaut, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), ou votre propre programme serveur personnalisé (objet métier). Un programme serveur est instancié sur le serveur et une référence au programme, ou *proxy*, est retournée.  
  
 Ce didacticiel utilise le programme de serveur par défaut :  
  
```vb
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "https://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Appeler le programme serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
