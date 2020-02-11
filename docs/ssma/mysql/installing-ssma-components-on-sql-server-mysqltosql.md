---
title: Installation des composants SSMA sur SQL Server (MySQLToSql) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA extension pack, Installation
ms.assetid: 6772d0c5-258f-4d7b-afb0-b5f810e71af1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 64040f4a0caf8253e6d6e8a3b00ff21e0cebe6d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68075349"
---
# <a name="installing-ssma-components-on-sql-server-mysqltosql"></a>Installation des composants SSMA sur SQL Server (MySQLToSql)
Outre l’installation de SSMA, vous devez également installer les composants sur l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces composants incluent le pack d’extension SSMA, qui prend en charge la migration des données et les fournisseurs MySQL pour activer la connectivité de serveur à serveur.  
  
## <a name="ssma-for-mysql-extension-pack"></a>SSMA pour MySQL Pack d’extension  
Le pack d’extension SSMA ajoute une base de données, **sysdb**, à l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance spécifiée de. Cette base de données contient les tables et les procédures stockées nécessaires à la migration des données.  
  
En outre, lorsque vous migrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SSMA crée des travaux de l’agent, lorsque le moteur de migration de données côté serveur est utilisé pour la migration des données.  
  
### <a name="prerequisites"></a>Conditions préalables requises  
Avant d’installer les composants du serveur SSMA pour MySQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sur, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou une version ultérieure.  
  
-   Le fournisseur client MySQL et la connectivité à la base de données MySQL que vous souhaitez migrer. Vous pouvez installer des fournisseurs à partir du média du produit MySQL ou du site Web MySQL.  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser doit être en cours d’exécution pendant l’installation. Cette valeur est utilisée pour remplir une liste des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’Assistant installation. Vous pouvez désactiver le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser après l’installation.  
  
    > [!NOTE]  
    > Si le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser est en cours d’exécution, mais que vous ne voyez toujours pas la liste des instances dans le programme d’installation, vous devez débloquer le port UDP 1434. Vous pouvez utiliser le pare-feu Windows pour débloquer temporairement le port, ou vous pouvez désactiver temporairement le pare-feu Windows. Vous devrez peut-être également désactiver temporairement le logiciel antivirus. Veillez à activer les pare-feu et les logiciels antivirus après l’installation.  
  
### <a name="installing-the-extension-pack"></a>Installation du pack d’extension  
Vous pouvez installer le pack d’extension à tout moment avant de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Pour installer le pack d’extension, vous devez être membre du rôle de serveur **sysadmin** sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Pour installer le pack d’extension**  
  
1.  Copie SSMA pour MySQL extension Pack. *n*. Installez. exe, où *n* est le numéro de build, sur l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Double-cliquez sur SSMA pour MySQL extension Pack. *n*. Installez. exe.  
  
3.  Dans la boîte de dialogue Bienvenue, cliquez sur **suivant**.  
  
4.  Dans la boîte de dialogue contrat de licence utilisateur final, lisez le contrat de licence. Si vous acceptez, activez la case à cocher **J’accepte les termes du contrat de licence** , puis cliquez sur **suivant**.  
  
5.  Dans la boîte de dialogue choisir le type d’installation, cliquez sur par **défaut**.  
  
6.  Dans la boîte de dialogue prêt pour l’installation, cliquez sur **installer**.  
  
7.  Dans la boîte de dialogue la première étape de l’installation est terminée, cliquez sur **suivant**.  
  
    Une nouvelle boîte de dialogue s’affiche, dans laquelle vous sélectionnez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de pour l’installation du pack d’extension.  
  
8.  Sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans laquelle vous allez migrer les schémas MySQL, puis cliquez sur **suivant**.  
  
    L’instance par défaut porte le même nom que l’ordinateur. Les instances nommées sont suivies d’une barre oblique inverse et du nom de l’instance.  
  
9. Dans la boîte de dialogue connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilise vos informations d’identification Windows pour essayer de se connecter à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un nom de connexion et un mot de passe.  
  
10. Dans la boîte de dialogue suivante, sélectionnez **installer la base de données des utilitaires** *n*, où *n* est le numéro de version, puis cliquez sur **suivant**.  
  
    La base de données **sysdb** est créée avec les tables et les procédures stockées requises pour la migration des données (à l’aide du moteur de migration de données côté serveur) sont créées dans cette base de données.  
  
11. Pour installer les utilitaires sur une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de, sélectionnez **Oui**, puis cliquez sur **suivant**. Ou, pour quitter l’Assistant, cliquez sur **non**.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour MySQL client &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Migration de bases de données MySQL vers SQL Server-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
