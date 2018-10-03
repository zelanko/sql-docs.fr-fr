---
title: Didacticiel RDS | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO]
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9a7538bb51ebe0a04a20aff81e83c3cc1ac92aa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747887"
---
# <a name="rds-tutorial"></a>Tutoriel RDS
Ce didacticiel illustre à l’aide du modèle de programmation RDS pour interroger et mettre à jour une source de données. Tout d’abord, il décrit les étapes nécessaires pour accomplir cette tâche. Ensuite, le didacticiel est répété dans Microsoft® Visual Basic Scripting Edition (présentant ADO pour Windows Foundation Classes (ADO/WFC)).  
  
 Ce didacticiel est codé dans différents langages pour deux raisons :  
  
-   La documentation pour les services Bureau à distance suppose que le lecteur code dans Visual Basic. Cela rend la documentation pratique pour les programmeurs Visual Basic, mais il est moins utile pour les programmeurs qui utilisent d’autres langages.  
  
-   Si vous avez des doutes sur une fonctionnalité particulière de services Bureau à distance et que vous connaissez un peu d’une autre langue, vous pourrez peut-être résoudre votre problème en recherchant cette même fonction exprimée dans une autre langue.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="how-the-tutorial-is-presented"></a>Présentation du didacticiel  
 Ce didacticiel est basé sur le modèle de programmation des services Bureau à distance. Il aborde individuellement chaque étape du modèle de programmation. En outre, il montre chaque étape avec un fragment de code Visual Basic.  
  
 L’exemple de code est répété dans d’autres langages avec un minimum de détails. Chaque étape dans un didacticiel du langage de programmation donné est marquée avec l’étape correspondante dans le modèle de programmation et le didacticiel descriptif. Utilisez le numéro de l’étape pour faire référence à la discussion dans le didacticiel descriptif.  
  
 Le modèle de programmation RDS est indiqué dans la section suivante. Utilisez-le comme une feuille de route pendant que vous suivez le didacticiel.  
  
## <a name="rds-programming-model-with-objects"></a>Modèle de programmation RDS avec des objets  
  
-   Spécifiez le programme à appeler sur le serveur et obtenir un moyen (proxy) pour faire référence à celui-ci à partir du client.  
  
-   Appeler le programme serveur. Passer des paramètres pour le programme de serveur qui identifie la source de données et de la commande à émettre.  
  
-   Le programme serveur obtient un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet à partir de la source de données, généralement à l’aide d’ADO. Si vous le souhaitez, le **Recordset** objet est traité sur le serveur.  
  
-   Le programme serveur retourne le dernier **Recordset** objet à l’application cliente.  
  
-   Sur le client, le **Recordset** objet est éventuellement placé dans un formulaire qui peut être facilement utilisé par des contrôles visuels.  
  
-   Modifications apportées à la **Recordset** objet sont envoyés sur le serveur et utilisées pour mettre à jour la source de données.  
  
 Ce didacticiel contient les rubriques suivantes.  
  
-   [Étape 1 : Spécifier un programme serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)  
  
-   [Étape 2 : Appeler le programme serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-2-invoke-the-server-program-rds-tutorial.md)  
  
-   [Étape 3 : Le serveur obtient un recordset (didacticiel RDS)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)  
  
-   [Étape 4 : Le serveur retourne un recordset (didacticiel RDS)](../../../ado/guide/remote-data-service/step-4-server-returns-the-recordset-rds-tutorial.md)  
  
-   [Étape 5 : DataControl devient utilisable (didacticiel RDS)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)  
  
-   [Étape 6 : Les changements sont envoyés au serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)  
  
-   [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Spécifier un programme serveur (didacticiel RDS)](../../../ado/guide/remote-data-service/step-1-specify-a-server-program-rds-tutorial.md)   
 [Didacticiel RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
