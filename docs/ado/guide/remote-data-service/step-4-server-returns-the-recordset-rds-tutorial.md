---
description: 'Étape 4 : Le serveur retourne un recordset (tutoriel RDS)'
title: 'Étape 4 : le serveur retourne le recordset (didacticiel RDS) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
author: rothja
ms.author: jroth
ms.openlocfilehash: 80db98699916cea22cd2815871f99159b1f1a7c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451921"
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Étape 4 : Le serveur retourne un recordset (tutoriel RDS)
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS convertit l’objet **Recordset** récupéré en un formulaire qui peut être renvoyé au client (autrement dit, il *marshale* le **Recordset**). La forme exacte de la conversion et la façon dont elle est envoyée varient selon que le serveur est sur Internet ou sur un intranet, un réseau local ou une bibliothèque de liens dynamiques. Toutefois, ce détail n’est pas critique. ce qui importe, c’est que RDS renvoie le **jeu d’enregistrements** au client.  
  
 Côté client, un objet **Recordset** est retourné et affecté à une variable locale.  
  
```vb
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 5 : le DataControl est rendu utilisable (didacticiel RDS)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [Tutoriel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
