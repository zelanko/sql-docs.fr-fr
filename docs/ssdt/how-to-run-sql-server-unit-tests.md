---
title: 'Guide pratique : Exécuter des tests unitaires SQL Server | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 34fe2d1e-d47b-4808-af56-8cc0fdae6518
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 276096d9e5ce082f31439e664614833eb68f6984
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083712"
---
# <a name="how-to-run-sql-server-unit-tests"></a>Procédure : exécuter des tests unitaires SQL Server
Il existe différents moyens d’exécuter un test unitaire SQL Server, notamment en utilisant plusieurs fenêtres et une fenêtre d’invite de commandes.  
  
> [!NOTE]  
> Vous ne pouvez pas exécuter des tests unitaires à distance.  
  
Les méthodes disponibles dépendent du logiciel installé – voir [Exécuter des tests unitaires SQL Server](../ssdt/running-sql-server-unit-tests.md).  
  
### <a name="to-run-sql-server-unit-tests-using-test-view-visual-studio-2010"></a>Exécuter des tests unitaires SQL Server avec l’Affichage des tests (Visual Studio 2010)  
  
1.  Dans le menu **Test**, pointez sur **Fenêtres**, puis cliquez sur **Affichage des tests**.  
  
    La fenêtre **Affichage des tests** s’ouvre.  
  
2.  Dans la fenêtre **Affichage des tests**, cliquez sur le ou les tests à exécuter. À l'aide de la touche Ctrl ou Maj, spécifiez des blocs discontinus ou continus de tests.  
  
3.  Effectuez l'une des opérations suivantes :  
  
    -   Cliquez avec le bouton droit sur la surface de la fenêtre **Affichage des tests**, puis cliquez sur **Exécuter la sélection**.  
  
    -   Dans la barre d’outils **Affichage des tests**, cliquez sur **Exécuter la sélection**.  
  
### <a name="to-run-sql-server-unit-tests-using-test-explorer-visual-studio-2012"></a>Exécuter des tests unitaires SQL Server avec l’Explorateur de tests (Visual Studio 2012)  
  
1.  Dans le menu **Test**, pointez sur **Fenêtres**, puis cliquez sur **Explorateur de tests**.  
  
    La fenêtre **Explorateur de tests** s’ouvre.  
  
2.  Dans **l’Explorateur de tests**, cliquez sur le ou les tests à exécuter. À l'aide de la touche Ctrl ou Maj, spécifiez des blocs discontinus ou continus de tests.  
  
3.  Cliquez avec le bouton droit sur un des tests sélectionnés, puis cliquez sur **Exécuter les tests sélectionnés**.  
  
### <a name="to-run-sql-server-unit-tests-from-the-sql-server-unit-test-designer-visual-studio-2010"></a>Exécuter des tests unitaires SQL Server avec le Concepteur de tests unitaires SQL Server (Visual Studio 2010)  
  
-   Dans la barre d’outils **Outils de test**, vous trouverez les boutons nécessaires pour commencer un projet avec ou sans débogueur.  
  
Cette étape exécute tous les tests d'une série de tests active. Dès que vous démarrez une série de tests, la fenêtre **Résultats des tests** apparaît et affiche la progression de la série de tests. Cet affichage comprend les tests en cours d'exécution et les tests qui ont été finalisés. Pour plus d’informations, voir [Interprétation des résultats des tests unitaires SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md).  
  
## <a name="see-also"></a> Voir aussi  
[Exécuter des tests unitaires SQL Server](../ssdt/running-sql-server-unit-tests.md)  
[Guide pratique : Exécuter des tests automatisés à partir de Microsoft Visual Studio 2010](http://msdn.microsoft.com/library/ms182470(VS.100).aspx)  
[Exécuter des tests automatisés en ligne de commande (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182486(VS.100).aspx)  
[Tester l’application (Visual Studio 2012)](http://msdn.microsoft.com/library/ms182409.aspx)  
  
