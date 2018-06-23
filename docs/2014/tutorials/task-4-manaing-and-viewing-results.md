---
title: 'Tâche 4 : Gestion et affichage des résultats | Documents Microsoft'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0e045d9722d380af19147746944c842f97ac9843
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154298"
---
# <a name="task-4-manaing-and-viewing-results"></a>Tâche 4 : Gestion et affichage des résultats
  Dans cette tâche, vous allez examiner les résultats du nettoyage assisté par ordinateur, et vous allez également effectuer un nettoyage interactif des données du fournisseur. Consultez [étape de nettoyage interactif](http://msdn.microsoft.com/library/hh213061.aspx#Interactive) pour plus d’informations.  
  
1.  Sélectionnez **messagerie du Contact** domaine à partir de la liste des domaines.  
  
2.  Basculez vers le **non valide** onglet dans le volet droit. Notez les deux adresses de messagerie dans lesquelles il manque le caractère « s » à la fin. Ces deux adresses électroniques qui ont été identifiés comme étant non valide par la règle de domaine qui nécessite toutes les adresses de messagerie se terminent par **@adventure-works.com** (avec de '). DQS utilise la règle de domaine lors du nettoyage afin de déterminer si une adresse électronique est valide ou non. Cet onglet affiche les valeurs de domaine qui ont été marquées comme non valides dans la base de connaissances, ou celles qui ne respectent pas une règle de domaine. Dans ce cas, ces valeurs ne respectent pas la règle de domaine (validation de l'adresse électronique).  
  
3.  Dans le **corriger vers** , entrez la bonne adresse d’adresses qui se terminent par **@adventure-works.com** (avec de ').  
  
     ![Corrections à partir de la règle de Validation d’E-mail](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Corrections à partir de la règle de Validation par courrier électronique")  
  
4.  Cliquez sur **approuver** pour les deux enregistrements approuver les modifications. Lorsque vous approuvez, les enregistrements sont déplacés vers le **corrigés** onglet. Au lieu d’approuver chaque élément séparément, vous pouvez approuver toutes les modifications apportées à la fois à l’aide de la **approuver tous les termes** bouton de barre d’outils.  
  
5.  Basculez vers le **nouveau** onglet dans le volet droit. Les valeurs de cet onglet sont les valeurs pour lesquelles DQS ne dispose pas encore de suffisamment d'informations dans la base de connaissances pour déterminer si elles sont correctes. Par conséquent, il ne peut pas modifier ou suggérer des modifications aux valeurs de domaine.  
  
6.  Passez en revue les valeurs pour vérifier que tous les e-mails se terminent par **@adventure-works.com** et cliquez sur **approuver tous les termes** sur la barre d’outils. Les valeurs approuvées à partir de cet onglet déplacent vers le **Correct** onglet.  
  
7.  Sélectionnez le **pays** domaine à partir de la liste des domaines.  
  
8.  Basculer vers le **corrigés** onglet dans le volet droit et remarquez que **United State** valeur est automatiquement corrigée par le **États-Unis** avec du ' à la fin. Cette règle n’est pas une règle que vous avez défini pour le **pays** domaine, mais DQS **83 %** avec la certitude que la valeur correcte est **États-Unis**. Le **approuver** bouton est sélectionné automatiquement pour tous les le **corrigés** éléments. Vous pouvez substituer ce comportement et rejeter une modification.  
  
9. Notez que **USA** est corrigé par **États-Unis** , car ils sont synonymes et **États-Unis** est la valeur de début (par défaut).  
  
     ![Corrections basées sur synonymes](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Corrections basées sur synonymes")  
  
10. Notez que la **approuver** bouton est déjà sélectionné pour ces valeurs corrigées. Il s'agit du comportement par défaut pour les valeurs corrigées. Vous pouvez rejeter une modification, et lorsque vous procédez ainsi, la valeur se déplace vers le **non valide** onglet.  
  
11. Sélectionnez **Supplier Name** à partir de la liste des domaines.  
  
12. Basculez vers le **corrigés** onglet dans le volet droit.  
  
     ![Noms corrigés des fournisseurs](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "noms corrigés des fournisseurs")  
  
    1.  Notez que **A. Datum Corp.** est corrigé par **A. Datum Corporation** et **raison** a la valeur **relation de base de termes. A. datum Corporation** est une valeur de domaine connu de DQS, car il a été détectée pendant le processus de découverte de connaissances. Par conséquent, DQS est **sûr à 100 %** sur cette correction.  
  
    2.  Notez que qui **Lazy Country Storex** est corrigé par **Lazy Country Store**, **un niveau de confiance** a la valeur **100 %** et le  **Raison** a la valeur **valeur de domaine**. Pendant le processus de découverte de connaissances, vous définissez **Lazy Country Storex** en tant qu’erreur avec **Lazy Country Store** comme le **correction**, et DQS **100 % certain** effectuer la correction.  
  
    3.  DQS n’est pas familiarisé avec les autres valeurs dans la liste, mais elle a trouvé les corrections de ces valeurs à l’aide de la **vérificateur d’orthographe** et propose les corrections appropriées. DQS est **pas 100 %** est sûr à ces corrections, mais le niveau de confiance supérieur à 80 %, ce qui est le niveau de seuil pour apporter des corrections, afin de DQS suggère les corrections.  
  
13. Notez que la **approuver** est automatiquement activé pour toutes les valeurs. Vous pouvez remplacer la valeur corrigée ou refuser la modification, comme il convient. Par défaut le **approuver** bouton est sélectionné pour toutes les valeurs dans le **corrigés** onglet.  
  
14. Basculez vers le **nouveau** onglet.  
  
15. Notez que **corp.** est corrigé par **Corporation**, **Co.** est corrigé par **société**, et **Inc.** est corrigé par **Incorporated**. Par exemple, **Consolidate Inc.** est corrigé par **Consolidate Incorporated** et **Consolidated Co.** est corrigé par **Consolidated Company**, et **Frabrikam corp.** est corrigé par **Fabrikam Corporation**.  Vous pouvez voir que **base de termes de relation** est indiquée comme raison. Ces modifications sont suggérées à l'aide des relations à base de termes que vous avez définies pendant l'activité de gestion de domaine. Vous pouvez modifier le **corriger vers** manuellement ici.  
  
16. Faites défiler la liste pour voir **Hunxgry Coyote Store** avec une ligne ondulée rouge. Avec le bouton droit dessus, puis cliquez sur **Hungy Coyote Store** (avec sans « x »). Le **corriger vers** colonne doit être automatiquement renseignée avec **Hungry Coyote Store**. Vous pouvez également entrer manuellement une valeur dans la colonne Corriger vers.  
  
17. Cliquez sur **approuver tous les termes** à partir de la barre d’outils. Les valeurs de domaine avec le **corriger vers** déplacer de valeur spécifiée pour le **corrigés** onglet et les nouvelles valeurs sans aucune associés **corriger vers** valeurs déplacent vers le  **Correct** onglet.  
  
18. Sélectionnez le **Validation d’adresses** domaine composite à partir de la liste des domaines.  
  
19. Dans le volet droit, basculez vers le **Correct** onglet. Vous devez voir les adresses qui sont jugées correctes par le **Melissa Data – contrôle d’adresse** service DQS sur le **Azure Marketplace**.  
  
20. Basculez vers le **corrigés** onglet.  
  
21. Notez que **état** pour l’enregistrement a **Ville** en tant que **Los Angeles** a la valeur **autorité de certification** maintenant. Notez que, dans le **raison** champ **corrigé par la règle 'Ville-Département Rule'**.  
  
     ![Correction de la règle Ville-Département](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "Correction de la règle Ville-Département")  
  
22. Notez que la **approuver** case d’option est déjà sélectionnée pour cet élément dans la liste. Il s’agit du comportement par défaut pour les éléments sur le **corrigés** onglet.  
  
23. Basculez vers le **suggérés** onglet. Passez en revue les modifications suggérées par le **Melissa Data – contrôle d’adresse** service.  
  
24. **Cliquez sur Approuver tous les termes** sur le bouton de barre d’outils et cliquez sur **OK** sur la **Confirmation** boîte de message.  
  
     ![Bouton de barre d’outils tous les termes du contrat approuver](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "approuver le bouton de barre d’outils tous les termes du contrat")  
  
25. Cliquez sur **suivant** pour basculer vers le **exporter** page.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 5 : Exportation des résultats du nettoyage vers un fichier Excel](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  