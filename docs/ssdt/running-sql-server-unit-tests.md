---
title: Exécution de tests unitaires SQL Server | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.unittesting.testconfig
ms.assetid: febcc87f-eb18-4c12-ba30-82ef0d49aaa3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35ed4fd4090a3a7ef5cff862817bbaec592749a3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51670678"
---
# <a name="running-sql-server-unit-tests"></a>Exécution de tests unitaires SQL Server
Pour améliorer et gérer la qualité de votre code, créez et exécutez des tests unitaires SQL Server qui vérifient le comportement d'un objet de base de données, puis archivez ces tests dans le contrôle de version. Lorsque vous ou un membre de l'équipe modifiez le schéma de la base de données, vous exécutez des tests unitaires SQL Server et des tests unitaires de logiciel pour vérifier que les modifications n'empêchent pas l'exécution des fonctionnalités existantes. Exécutez des tests individuels ou des groupes de tests, appelés listes de tests. Pour plus d'informations, consultez [Utilisation de listes de tests (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182461(VS.100).aspx).  
  
## <a name="ways-to-run-sql-server-unit-tests"></a>Manières d’exécuter des tests unitaires SQL Server  
Vous pouvez effectuer des tests unitaires SQL Server de plusieurs façons, en fonction du logiciel que vous avez installé, comme suit :  
  
-   Exécutez des tests à l’aide de la fenêtre Visual Studio 2010**Affichage des tests**. Pour plus d'informations, consultez [Procédure : exécuter des tests unitaires SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md) et [Procédure : exécuter des tests automatisés à partir de Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx). Pour Visual Studio 2012, consultez [Procédure : exécuter des tests automatisés à partir de Microsoft Visual Studio 2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Exécutez des tests à l'aide de la commande MSTest.exe à l'invite de commandes. Pour plus d'informations, consultez [Procédure : exécuter des tests automatisés à partir de la ligne de commande à l'aide de MSTest (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182487(VS.100).aspx) or [Procédure : exécuter des tests automatisés à partir de la ligne de commande à l'aide de MSTest (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182487.aspx).  
  
-   Exécutez des tests dans l'**Explorateur de solutions** en exécutant un projet de test. Pour plus d'informations, consultez [Procédure : exécuter des tests automatisés à partir de Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx) ou [Procédure : exécuter des tests automatisés à partir de Microsoft Visual Studio 2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Réexécutez des tests dans la fenêtre **Résultats des tests**. Pour plus d'informations, consultez [Procédure : réexécuter un test (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
-   Exécutez des tests individuels ou des listes de tests (Visual Studio 2010) dans la fenêtre **Explorateur de tests**. Pour plus d'informations, consultez [Procédure : exécuter des tests automatisés à partir de Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx) ou [Procédure : exécuter des tests automatisés à partir de Microsoft Visual Studio 2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Exécutez des tests à mesure que vous créez un projet dans Team Foundation Build. Pour plus d'informations, consultez [Procédure : configurer et exécuter des tests planifiés après avoir généré votre application (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182465(VS.100).aspx) or [Procédure : configurer et exécuter des tests planifiés après avoir généré votre application (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182465.aspx).  
  
Exécutez vos tests unitaires SQL Server dans un ordre particulier à l'aide d'un test ordonné. Pour plus d'informations, consultez [Procédure : créer un test ordonné (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182631(VS.100).aspx) ou [Procédure : créer un test ordonné (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182631.aspx).  
  
## <a name="interpreting-tests-results"></a>Interprétation des résultats de tests  
Après avoir exécuté vos tests, la fenêtre **Résultats des tests** indique les tests ayant réussi ou échoué. Pour plus d’informations, voir [Interprétation des résultats des tests unitaires SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md). Pour plus d'informations sur la façon de diagnostiquer une erreur inattendue, consultez [Procédure : déboguer des objets de base de données](../ssdt/how-to-debug-database-objects.md).  
  
## <a name="topics-in-this-section"></a>Rubriques de cette section  
Cette section contient les rubriques suivantes :  
  
-   [Procédure : déboguer des objets de base de données](../ssdt/how-to-debug-database-objects.md)  
  
-   [Procédure : exécuter des tests unitaires SQL Server en utilisant Team Foundation Build](../ssdt/how-to-run-sql-server-unit-tests-from-team-foundation-build.md)  
  
-   [Procédure : exécuter des tests unitaires SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md)  
  
-   [Interprétation des résultats des tests unitaires SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md)  
  
## <a name="related-scenarios"></a>Scénarios connexes  
[Création et définition de tests unitaires SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
Définissez des tests unitaires pour vérifier le comportement des objets de base de données et pour associer chaque projet de test à un plan de génération de données, une configuration de déploiement et une chaîne de connexion différents.  
  
[Conditions de test personnalisées pour les tests unitaires SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
Créez une condition de test personnalisée afin déterminer toute condition que vous ne pouvez pas vérifier en utilisant des conditions de test par défaut.  
  
## <a name="see-also"></a> Voir aussi  
[Vérifier le code de la base de données à l’aide de tests unitaires SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
