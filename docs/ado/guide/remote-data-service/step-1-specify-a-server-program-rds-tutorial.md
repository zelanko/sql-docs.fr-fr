---
title: 'Étape 1 : Spécifier un programme serveur (didacticiel RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], specifying server program
ms.assetid: d8bb35b1-c02a-4231-8d55-016e56e53b95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dd842dd689b8aa15203f0918c44b7047831bb93
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732267"
---
# <a name="step-1-specify-a-server-program-rds-tutorial"></a>Étape 1 : Spécifier un programme serveur (tutoriel RDS)
Dans la plupart des cas, utilisez le [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) méthode pour spécifier le programme de serveur par défaut, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md), ou votre propre programme serveur personnalisé (objet métier). Un programme serveur est instancié sur le serveur et une référence au programme, ou *proxy*, est retournée.  
  
 Ce didacticiel utilise le programme de serveur par défaut :  
  
```  
Sub RDSTutorial1()  
   Dim DS as New RDS.DataSpace  
   Dim DF as Object  
   Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
...  
```  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Appeler le programme serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)   
 [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
