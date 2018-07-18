---
title: 'Tâche 12 : Découverte des connaissances (découverte des connaissances) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 04508f02f6e7bf2daa19117406cace4944a32d36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317419"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>Tâche 12 : Découverte des connaissances
  Dans cette tâche, vous allez effectuer la **découverte des connaissances** activité sur **ID du fournisseur** et **Supplier Name** domaines. Dans ce scénario, le processus de découverte des connaissances importe principalement des valeurs pour ces deux domaines.  
  
 Dans ce didacticiel, vous avez commencé à créer une base de connaissances de toutes pièces. Vous pouvez également créer une base de connaissances au moyen d'une activité de découverte des connaissances. Lorsque vous cliquez sur **créer une Base de connaissances** dans la page principale, le client DQS pointe vers une page avec **gestion des domaines** activité sélectionnée pour l’activité. Vous pouvez modifier le **activité** à **découverte des connaissances** et puis dans la page suivante vous pouvez créer des domaines dans le cadre du processus de découverte de connaissances. Consultez [Perform Knowledge Discovery](http://msdn.microsoft.com/library/hh510398.aspx) pour plus d’informations.  
  
1.  Dans la page principale du Client DQS, dans le **Base de connaissances récente** , cliquez sur **flèche droite** à côté du **fournisseurs** base de connaissances et cliquez sur **connaissances Découverte**. Vous pouvez également cliquer sur **ouvrir la Base de connaissances**, sélectionnez **fournisseurs** à partir de la **liste des bases de connaissances**, sélectionnez **la découverte des connaissances**en tant que **activité** et cliquez sur **suivant**.  
  
     ![Menu de découverte de connaissances principal Page](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Menu de découverte de connaissances principal Page")  
  
2.  Sélectionnez **un fichier Excel** pour **Source de données**.  
  
3.  Cliquez sur **Parcourir**, naviguez et sélectionnez **Suppliers.xls**, puis cliquez sur **Open**.  
  
4.  Sélectionnez **fournisseurs pour la découverte** pour **feuille de calcul**.  
  
5.  Dans le **mappages** section, mappez **SupplierID** colonne à partir de la **Excel** de fichiers à la **ID du fournisseur** domaine et  **Nom du fournisseur** colonne à la **Supplier Name** domaine à l’aide de **listes déroulantes**. Le fichier Excel propose des exemples de données pour le **ID du fournisseur** et **Supplier Name** domaines. Dans le processus de découverte, vous pouvez sélectionner les domaines dont vous souhaitez connaître les valeurs. Vous pouvez créer des domaines dans cette page, puis mapper les colonnes sources à ces domaines. Il n'est pas rare de créer des domaines pendant l'activité de découverte des connaissances au lieu de créer des domaines pendant l'activité de gestion de domaine.  
  
     ![Page du processus de détection de mappage](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Page du processus de détection de mappage")  
  
6.  Cliquez sur **suivant** pour basculer vers le **Discover** page.  
  
7.  Sur le **Discover** , cliquez sur **Démarrer** pour démarrer le processus de découverte. Découverte est exécutée sur les colonnes **SupplierID** et **Supplier Name** dans le **Suppliers.xls** fichier. Le **ID du fournisseur** et **Supplier Name** domaines doivent être remplis avec les connaissances acquises grâce à la découverte.  
  
     ![Page de processus de découverte découverte](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "découvrir Page du processus de détection")  
  
8.  Une fois l’analyse terminée, passez en revue la **statistiques sources** dans le **onglet de Profiler** en bas de la page. Notez que 10 nouveaux enregistrements avec les 20 valeurs au total (**SupplierID** et **Supplier Name** valeurs à partir de la **feuille de calcul Excel**) ont été découvertes. Notez également combien de valeurs sont nouvelles, uniques, nouvelles et uniques, et valides. Dans la zone de liste située à droite, vous pouvez obtenir plus de détails sur chaque domaine impliqué dans le processus de découverte. Si vous pointez la souris sur la barre d'état de la colonne Exhaustivité, vous pouvez voir s'il existe des valeurs manquantes dans les colonnes de la source.  
  
     ![Résultats de découverte des connaissances](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "des résultats de découverte de connaissances")  
  
9. Cliquez sur **suivant** pour basculer vers le **gérer les valeurs du domaine** page.  
  
10. Dans le **gérer les valeurs du domaine** , cliquez sur **Supplier Name** domaine à partir de la liste des domaines.  
  
11. Dans le volet droit, cliquez sur **Lazy Country Storex** (Notez que « x » à la fin), puis sélectionnez **Lazy Country Store**. DQS suggère cette modification après avoir appliqué le vérificateur d'orthographe au domaine. Par défaut, le vérificateur d'orthographe est appliqué aux domaines que vous créez.  
  
     ![Corriger le nom de fournisseur - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "corriger le nom du fournisseur - Lazy Country Store")  
  
12. Dans la liste de valeurs de domaine, vérifiez que la valeur **Lazy Country Storex** est défini comme une erreur (rouge **X** marquer) avec **Lazy Country Store** en tant que la correction et également le **Lazy Country Store** est également ajouté en tant qu’une valeur valide.  
  
     ![Domaine de valeur et de corriger à la valeur](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "domaine valeur et à corriger à la valeur")  
  
13. Cliquez sur **Terminer**.  
  
14. Sur **SQL Server Data Quality Services** boîte de dialogue, cliquez sur **publier**.  
  
15. Cliquez sur **OK** sur la boîte de message de réussite.  
  
     Vous avez terminé la première leçon du didacticiel.  
  
## <a name="next-step"></a>Étape suivante  
 [Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
