---
description: 'Leçon 4-2 : Créer un fichier endommagé'
title: 'Étape 2 : Créer un fichier endommagé | Microsoft Docs'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81bee95c84aabe02f2964f41849051a7c8c7052a
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88449631"
---
# <a name="lesson-4-2-create-a-corrupted-file"></a>Leçon 4-2 : Créer un fichier endommagé

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Pour démontrer l’utilisation des fonctions de configuration et de gestion des erreurs de transformation, vous avez besoin d’un exemple de fichier plat qui, lors de son traitement, entraîne l’échec d’un composant.  
  
Au cours de cette tâche, vous créez une copie d’un fichier plat existant. Ensuite, vous ouvrez le fichier dans le Bloc-notes, puis modifiez la colonne **CurrencyID** afin qu’elle contienne une valeur erronée, ce qui entraînera l’échec de la recherche. Lors du traitement du fichier endommagé, l’échec de la recherche provoque à son tour l’échec de la transformation Lookup Currency Key et, donc, celui du reste du package. Une fois le fichier exemple endommagé créé, vous exécutez le package pour examiner son échec.  
  
## <a name="create-a-corrupted-sample-flat-file"></a>Créer un fichier plat exemple endommagé  
  
1.  Dans le Bloc-notes ou un autre éditeur de texte, ouvrez le fichier **Currency_VEB.txt**.  
  
2.  Utilisez la fonction Rechercher/Remplacer de l'éditeur de texte pour retrouver toutes les instances de **VEB** et les remplacer par **BAD**.  
  
3.  Dans le dossier qui contient les autres exemples de fichiers de données, enregistrez le fichier modifié en tant que **Currency_BAD.txt**.  
  
    > [!NOTE]  
    > Vérifiez que vous enregistrez **Currency_BAD.txt** dans le même dossier que les autres exemples de fichiers de données.  
  
4.  Fermez l'éditeur de texte.  
  
## <a name="verify-that-an-error-occurs-during-run-time"></a>Vérifier qu’une erreur se produit au moment de l’exécution  
  
1.  Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.  
  
    À la troisième itération du flux de données, la transformation Lookup Currency Key tente de traiter le fichier **Currency_BAD.txt** et la transformation échoue. L’échec de la transformation entraîne l’échec de tout le package.  
  
2.  Dans le menu **Déboguer**, sélectionnez **Arrêter le débogage**.  
  
3.  Dans la zone de conception, sélectionnez l’onglet **Résultats d’exécution**.  
  
4.  Parcourez le journal et vérifiez si les erreurs non gérées suivantes se sont produites :  
  
    ```
    [Lookup Currency Key[27]] Error: Row yielded no match during lookup.
    ```
  
    > [!NOTE]  
    > Le nombre 27 désigne l'ID du composant. Cette valeur est attribuée lors de la création du flux de données ; la valeur définie dans votre package peut être différente.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante  
[Étape 3 : Ajouter une redirection de flux d’erreurs](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
  
  
