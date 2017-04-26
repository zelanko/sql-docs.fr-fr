---
title: "Accès hors connexion à la documentation de SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 08/22/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 257ed357-8cbb-43bd-b042-254be5fbb977
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1266b0249a96fbc4828b2afee9fb218682501e4d
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-documentation-offline-access"></a>Accès hors connexion à la documentation de SQL Server

Consultez la documentation technique de SQL Server 2016 hors connexion.
  
## <a name="prerequisites"></a>Prérequis
Pour afficher la documentation technique de SQL Server 2016 hors connexion, vous avez besoin de HelpViewer 2.2, qui est installé avec : 
- [Visual Studio 2015 (toute édition, notamment Community)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) ou
- [SQL Server Management Studio (SSMS), préversion d’avril 2016 (13.0.12500.29) ou version ultérieure](https://msdn.microsoft.com/library/mt238290.aspx)

Installez l’un de ces deux produits avant de procéder aux étapes suivantes.
  
## <a name="install-sql-server-offline-technical-documentation"></a>Installer la documentation technique hors connexion de SQL Server 

1. Installez n’importe quelle édition de Visual Studio 2015 ou SSMS (préversion d’avril 2016 ou version ultérieure). 
2. Lancez SSMS ou Visual Studio.
3. Dans le menu **Aide** le long de la barre de navigation supérieure, sélectionnez  **Ajouter et supprimer le contenu d’aide**. 

#### <a name="this-action-launches-the-helpviewer"></a>(Cette action lance HelpViewer.)

4. Dans HelpViewer, choisissez la source d’installation par défaut : **En ligne** 
5. Cliquez sur **Ajouter** en regard de toute la documentation que vous souhaitez installer.
6. Cliquez sur le bouton **Mise à jour** situé en bas à droite de l’écran pour télécharger et installer la documentation sélectionnée.
![charger du contenu hors connexion](../sql-server/media/load-offline-content.png) 

 >**IMPORTANT !** Une fois que vous avez cliqué sur Mise à jour, HelpViewer se fige après un certain laps de temps. Néanmoins, il a quand même téléchargé et installé vos choix de documentation. **Pour résoudre ce problème**, fermez HelpViewer dans le Gestionnaire des tâches, puis redémarrez-le en suivant l’étape 3 ci-dessus. La première fois que HelpViewer se fige, suivez également [ces étapes](https://msdn.microsoft.com/library/mt654096.aspx) . Vous ne devez effectuer ces étapes qu’une seule fois, mais vous devrez probablement fermer HelpViewer dans le Gestionnaire des tâches chaque fois que vous mettrez à jour votre contenu.  
6. Redémarrez HelpViewer en resélectionnant Aide/Ajouter et supprimer le contenu d’aide. Votre document hors connexion est maintenant disponible.



   ![Hors connexion disponible](../sql-server/media/offline-ready-to-use.png)




