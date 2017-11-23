---
title: "Étape 4 : Le serveur retourne l’objet Recordset (didacticiel RDS) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b607faa566bf584e1a18acb2ed6970f2e45d4404
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Étape 4 : Le serveur retourne le jeu d’enregistrements (didacticiel sur les services Bureau à distance)
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS convertit extraites **Recordset** objet à un formulaire qui peut être envoyé au client (autrement dit, il *marshale* le **Recordset**). La forme exacte de la conversion et la façon dont il est envoyé varie selon que le serveur se trouve sur Internet ou un intranet, un réseau local, ou est une bibliothèque de liens dynamiques. Toutefois, ce détail n’est pas critique ; l’important est que RDS envoie le **Recordset** au client.  
  
 Du côté client, un **Recordset** objet est retourné et affecté à une variable locale.  
  
```  
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 5 : DataControl est effectuée utilisable (didacticiel sur les services Bureau à distance)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
