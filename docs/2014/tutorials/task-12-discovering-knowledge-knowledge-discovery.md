---
title: 'Tâche 12 : découverte des connaissances (découverte des connaissances) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0bad2760a5dc9b16b24d75bb35617759543205f3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064774"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>Tâche 12 : Découverte des connaissances
  Au cours de cette tâche, vous allez effectuer l’activité de **découverte des connaissances** sur les domaines **ID du fournisseur** et nom du **fournisseur** . Dans ce scénario, le processus de découverte des connaissances importe principalement des valeurs pour ces deux domaines.  
  
 Dans ce didacticiel, vous avez commencé à créer une base de connaissances de toutes pièces. Vous pouvez également créer une base de connaissances au moyen d'une activité de découverte des connaissances. Lorsque vous cliquez sur **créer une base de connaissances** dans la page principale, le client DQS vous amène à une page avec l’activité de **gestion de domaine** sélectionnée pour l’activité. Vous pouvez modifier l' **activité** en **découverte des connaissances** , puis dans la page suivante, vous pouvez créer des domaines dans le cadre du processus de découverte des connaissances. Pour plus d’informations, consultez [effectuer une découverte des connaissances](https://msdn.microsoft.com/library/hh510398.aspx) .  
  
1.  Dans la page principale du client DQS, dans la section **base de connaissances récente** , cliquez sur la **flèche droite** en regard de la base de connaissances **fournisseurs** , puis cliquez sur **découverte des connaissances**. Vous pouvez également cliquer sur **ouvrir la base de connaissances**, sélectionnez **fournisseurs** dans la **liste des bases de connaissances**, sélectionnez **découverte des connaissances** comme **activité** , puis cliquez sur **suivant**.  
  
     ![Menu Découverte des connaissances dans la Page principal](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Menu Découverte des connaissances dans la Page principal")  
  
2.  Sélectionnez **fichier Excel** pour **source de données**.  
  
3.  Cliquez sur **Parcourir**, naviguez et sélectionnez **Suppliers.xls**, puis cliquez sur **ouvrir**.  
  
4.  Sélectionnez **fournisseurs pour la détection** de la **feuille de calcul**.  
  
5.  Dans la section **mappages** , mappez la colonne **RéfFournisseur** du fichier **Excel** vers la colonne **ID du fournisseur** et nom du **fournisseur** au domaine **nom du fournisseur** à l’aide des **listes déroulantes**. Le fichier Excel contient des exemples de données pour les domaines **ID du fournisseur** et **nom du fournisseur** . Dans le processus de découverte, vous pouvez sélectionner les domaines dont vous souhaitez connaître les valeurs. Vous pouvez créer des domaines dans cette page, puis mapper les colonnes sources à ces domaines. Il n'est pas rare de créer des domaines pendant l'activité de découverte des connaissances au lieu de créer des domaines pendant l'activité de gestion de domaine.  
  
     ![Page de mappage du processus de découverte](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Page de mappage du processus de découverte")  
  
6.  Cliquez sur **suivant** pour basculer vers la page de **découverte** .  
  
7.  Dans la page **découverte** , cliquez sur **Démarrer** pour démarrer le processus de découverte. La détection est effectuée sur les colonnes **RéfFournisseur** et le **nom du fournisseur** dans le fichier **Suppliers.xls** . Les domaines **ID du fournisseur** et nom du **fournisseur** doivent être remplis avec les connaissances tirées de la découverte.  
  
     ![Page de découverte du processus de découverte](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "Page de découverte du processus de découverte")  
  
8.  Une fois l’analyse terminée, examinez les **statistiques sources** dans l' **onglet générateur de profils** au bas de la page. Notez que 10 nouveaux enregistrements avec 20 valeurs au total (**RéfFournisseur** et les valeurs de **nom de fournisseur** de la feuille de **calcul Excel**) ont été découverts. Notez également combien de valeurs sont nouvelles, uniques, nouvelles et uniques, et valides. Dans la zone de liste située à droite, vous pouvez obtenir plus de détails sur chaque domaine impliqué dans le processus de découverte. Si vous pointez la souris sur la barre d'état de la colonne Exhaustivité, vous pouvez voir s'il existe des valeurs manquantes dans les colonnes de la source.  
  
     ![Résultats de la Découverte des connaissances](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Résultats de la Découverte des connaissances")  
  
9. Cliquez sur **suivant** pour passer à la page **gérer les valeurs du domaine** .  
  
10. Dans la page **gérer les valeurs du domaine** , cliquez sur nom du **fournisseur** domaine dans la liste des domaines.  
  
11. Dans le volet droit, cliquez avec le bouton droit sur **paresseux Country storex** (voir « x » à la fin), puis sélectionnez **paresseal Country Store**. DQS suggère cette modification après avoir appliqué le vérificateur d'orthographe au domaine. Par défaut, le vérificateur d'orthographe est appliqué aux domaines que vous créez.  
  
     ![Corriger le nom du fournisseur - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "Corriger le nom du fournisseur - Lazy Country Store")  
  
12. Dans la liste des valeurs de domaine, vérifiez que la valeur **Lazy Country storex** est définie comme une erreur (Red **X** Mark) avec le **magasin de pays paresseux** comme correction et que le **magasin des pays paresseux** est également ajouté en tant que valeur valide.  
  
     ![Valeur de domaine et corriger à la valeur](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Valeur de domaine et corriger à la valeur")  
  
13. Cliquez sur **Terminer**.  
  
14. Dans **SQL Server Data Quality Services** boîte de dialogue, cliquez sur **publier**.  
  
15. Cliquez sur **OK** dans la boîte de message de réussite.  
  
     Vous avez terminé la première leçon du didacticiel.  
  
## <a name="next-step"></a>étape suivante  
 [Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
