---
title: Fichiers de tests unitaires SQL Server | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cee093c9-b97d-4fb0-b80f-806d071259dc
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e23304a429b77bcb4a5fc6a4c1001f2f28cf7885
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094236"
---
# <a name="sql-server-unit-test-files"></a>Fichiers de tests unitaires SQL Server
Comme les tests unitaires de code managé, les tests unitaires SQL Server résident dans des projets de test. Affichez les éléments qui composent un test unitaire SQL Server dans la hiérarchie d'un projet de test de l'**Explorateur de solutions**.  
  
Un test unitaire SQL Server est constitué de plusieurs éléments contenus dans plusieurs fichiers. Le tableau suivant décrit les fichiers qui interagissent pour constituer un test unitaire SQL Server.  
  
|**Fichier**|**Description**|  
|------------|-------------------|  
|.cs ou .vb|Ce fichier de code source contient une classe décorée avec l'attribut [TestClass]. Cette classe contient une seule méthode de test pour les tests unitaires SQL Server à relation contenant-contenu. Ces méthodes sont décorées avec l'attribut [TestMethod].<br /><br />Chaque méthode de test contient le code approprié pour utiliser le script de test Transact\-SQL. Ce code est généré lorsque les méthodes de test sont créées, et vous pouvez le modifier.<br /><br />**REMARQUE :** si vous double-cliquez sur ce fichier dans l'**Explorateur de solutions**, la classe de test s'ouvre dans le Concepteur de test unitaire. Pour ouvrir le fichier .cs ou .vb et afficher son code source, dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier, puis cliquez sur **Afficher le code**.|  
|.resx|Ce fichier de ressources contient des scripts Transact\-SQL pour tous les tests figurant dans le fichier .cs ou .vb associé. Ce groupe de scripts inclut le script de prétest, le script de test et le script post-test. Le fichier de ressources contient le XML, que vous pouvez modifier. Le fichier de ressources est compilé dans l'assembly de test.<br /><br />Vous devez coder les scripts Transact\-SQL à l'aide du **Concepteur de test unitaire SQL Server**. Pour plus d’informations sur les scripts qui sont utilisés dans les tests unitaires SQL Server, consultez [Scripts dans les Tests unitaires SQL Server](../ssdt/scripts-in-sql-server-unit-tests.md).|  
|app.config|Ce fichier stocke les chaînes de connexion de base de données pour le projet de test, en plus des autres paramètres de configuration de test unitaire SQL Server, tels que le délai d'attente de commande. Pour plus d’informations, consultez [Scripts des tests unitaires SQL Server](../ssdt/scripts-in-sql-server-unit-tests.md).|  
|SQLDatabaseSetup.cs ou SQLDatabaseSetup.vb|Ce fichier contient une classe qui prépare l'environnement de test de tous les tests unitaires SQL Server du projet de test. Selon les paramètres de configuration dans le fichier app.config, un projet de base de données SQL Server peut être déployé dans la base de données de test.|  
  
## <a name="see-also"></a> Voir aussi  
[Création et définition de tests unitaires SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Création et définition de tests unitaires SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Vérification du code de la base de données à l'aide de tests unitaires SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
[Scripts des tests unitaires SQL Server](../ssdt/scripts-in-sql-server-unit-tests.md)  
  
