---
title: Installation des composants SSMA sur SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 10/01/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 1f0cea859e9465eebefebc061ee51107dc7844aa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71713310"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Installation des composants SSMA sur SQL Server (OracleToSQL)

Outre l’installation de SSMA, vous devez également installer les composants sur l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces composants incluent le pack d’extension SSMA, qui prend en charge la migration des données et les fournisseurs Oracle pour activer la connectivité de serveur à serveur.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA pour le pack d’extension Oracle

Le pack d’extension SSMA ajoute les bases de données **sysdb** et **ssmatesterdb** à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]spécifiée de. La base de données **sysdb** contient les tables et les procédures stockées requises pour migrer des données et les fonctions définies par l’utilisateur qui émulent les fonctions système Oracle. La base de données **ssmatesterdb** contient les tables et les procédures requises par le composant testeur.  
  
En outre, lorsque vous migrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SSMA crée des travaux de l’agent lorsque le moteur de migration de données côté serveur est utilisé pour la migration des données.  
  
### <a name="prerequisites"></a>Prérequis

Avant d’installer les composants SSMA pour Oracle Server sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assurez-vous que le système répond aux exigences suivantes :  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l’instance est installée. SSMA ne prend pas en charge SQL Server édition Express 2008.
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou une version ultérieure.  
  
- Le fournisseur client Oracle ou le fournisseur de OLE DB pour Oracle, ainsi que la connectivité à la base de données Oracle que vous souhaitez migrer. Vous pouvez installer des fournisseurs à partir du support produit Oracle ou d’un site Web Oracle.  
  
- Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser doit être en cours d’exécution pendant l’installation. Cette valeur est utilisée pour remplir une liste des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’Assistant installation. Vous pouvez désactiver le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser après l’installation.  
  
    > [!NOTE]  
    > Si le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Browser est en cours d’exécution, mais que vous ne voyez toujours pas la liste des instances dans le programme d’installation, vous devez débloquer le port UDP 1434. Vous pouvez utiliser le pare-feu Windows pour débloquer temporairement le port, ou vous pouvez désactiver temporairement le pare-feu Windows. Vous devrez peut-être également désactiver temporairement le logiciel antivirus. Veillez à activer les pare-feu et les logiciels antivirus après l’installation.  
  
### <a name="installing-the-extension-pack"></a>Installation du pack d’extension

Vous pouvez installer le pack d’extension à tout moment avant de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrer des données vers.  
  
> [!IMPORTANT]  
> Pour installer le pack d’extension, vous devez être membre du rôle de serveur **sysadmin** sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Pour installer le pack d’extension**
  
1. Si vous ne l’avez pas déjà fait, extrayez tous les fichiers du fichier zip SSMA.  
  
    Selon la version de WinZip que vous possédez, vous pouvez double-cliquer sur le fichier ou cliquer avec le bouton droit sur le fichier, puis sélectionner **extraire tout** ou **ouvrir dans WinZip**. Suivez les instructions de l’interface utilisateur WinZip pour extraire les fichiers.  
  
2. Copier **SSMA pour le pack d’extension Oracle.* n*. Install. exe** (où *n* est le numéro de Build) sur l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3. Double-cliquez sur **SSMA pour le pack d’extension Oracle.* n*. Installez. exe**.  
  
4. Sur la page d’**accueil**, sélectionnez **Suivant**.  
  
5. Sur la page **contrat de licence utilisateur final** , lisez le contrat de licence. Si vous acceptez, activez la case à cocher **J’accepte les termes du contrat de licence** , puis sélectionnez **suivant**.  
  
6. Dans la page **choisir le type d’installation** , sélectionnez **standard**.  
  
7. Sur la page **prêt pour l’installation** , sélectionnez **installer**.  
  
8. Dans la page **fin de la première étape de l’installation** , sélectionnez **suivant**.  
  
    Une nouvelle boîte de dialogue s’affiche, dans laquelle vous sélectionnez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de pour l’installation du pack d’extension.  
  
9. Sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers laquelle vous allez migrer des schémas Oracle, puis sélectionnez **suivant**.  
  
    L’instance par défaut porte le même nom que l’ordinateur. Les instances nommées sont suivies d’une barre oblique inverse et du nom de l’instance.  
  
10. Sur la page connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilise vos informations d’identification Windows pour essayer de vous connecter à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un nom de connexion et un mot de passe.  
  
11. Sur la page suivante, sélectionnez **installer la base de données des utilitaires** *n*, où *n* est le numéro de version, puis sélectionnez **suivant**.  
  
    La base de données **sysdb** est créée et les fonctions définies par l’utilisateur et les procédures stockées sont créées dans cette base de données.  
  
    Si l’option **installer la base de données du testeur** est cochée, la base de données **ssmatesterdb** du testeur est créée.  
  
12. Pour installer les utilitaires sur une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de, sélectionnez **Oui**, puis cliquez sur **suivant**, ou pour quitter l’Assistant, sélectionnez **non**.  
  
13. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l’aide de l’utilitaire sqlcmd, exécutez le script suivant pour activer le CLR :  
  
    ```
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```

    Si le CLR n’est pas activé, vous recevrez l’erreur suivante lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SSMA se connecte à :  
  
    SSMA n’a pas pu récupérer les informations de version de l’assembly du pack d’extension. Réinstallez le pack d’extension sur le serveur de base de données.  
  
### <a name="sql-server-database-objects"></a>SQL Server les objets de base de données  

Une fois que vous avez installé le pack d’extension, une table **ssma_oracle. bcp_migration_packages** apparaît dans la base de données **sysdb** .

Chaque fois que vous migrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données vers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSMA crée un travail de l’agent. Ces travaux sont nommés **ssma_oracle package de migration de données {GUID}** et sont visibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le nœud agent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] de dans le dossier travaux.  
  
## <a name="see-also"></a>Voir aussi

[Installation de SSMA pour Oracle client &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Migration de bases de données Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
