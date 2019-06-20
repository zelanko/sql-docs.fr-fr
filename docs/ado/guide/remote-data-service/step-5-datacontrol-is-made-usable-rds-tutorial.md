---
title: 'Étape 5 : DataControl est devient utilisable (didacticiel RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f654bc1ccd913c5fc31f81cae67ffdb84e80f952
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704154"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Étape 5 : DataControl devient utilisable (tutoriel RDS)
Retourné **Recordset** objet est disponible pour utilisation. Vous pouvez examiner, accédez ou le modifier comme vous le feriez pour n’importe quel autre **Recordset**. Vous pouvez faire avec le **Recordset** dépend de votre environnement. Visual Basic et Visual C++ ont des contrôles visuels que vous peuvent utiliser un **Recordset** directement ou indirectement à l’aide d’un contrôle d’activation de données.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Par exemple, si vous affichez une page Web dans Microsoft Internet Explorer, vous souhaiterez afficher le **Recordset** l’objet de données dans un contrôle visuel. Les contrôles visuels d’une page Web ne peut pas accéder à un **Recordset** directement l’objet. Toutefois, ils peuvent accéder à la **Recordset** via la [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). Le **RDS. DataControl** peut être utilisé par un élément visuel contrôle lorsque ses [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) propriété est définie sur le **Recordset** objet.  
  
 L’objet de contrôle visuel doit avoir son **DATASRC** paramètre défini sur le **RDS. DataControl**et son **DATAFLD** propriété définie sur une **Recordset** champ (colonne) de l’objet.  
  
 Dans ce didacticiel, définissez la **SourceRecordset** propriété :  
  
```vb
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 6 : Les modifications sont envoyées au serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
