---
title: Installation des composants SSMA sur SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2041901a851ca755b1079535ccbf763472ec7bc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853357"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Installation des composants SSMA sur SQL Server (OracleToSQL)
Outre l’installation de SSMA, vous devez également installer les composants sur l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces composants incluent le pack d’extension SSMA qui prend en charge la migration des données et les fournisseurs Oracle pour permettre la connectivité du serveur à serveur.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA pour Oracle le Pack d’Extension  
Le pack d’extension SSMA ajoute les bases de données, **sysdb** et **ssmatesterdb**, à l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La base de données **sysdb** contient les tables et procédures stockées qui sont nécessaires pour migrer des données et les fonctions définies par l’utilisateur qui émulent des fonctions du système Oracle. Le **ssmatesterdb** base de données contient les tables et les procédures qui sont requis par le composant de testeur.  
  
En outre, lorsque vous migrez des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA crée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travaux de l’Agent lorsque le moteur de migration de données côté serveur est utilisé pour migrer les données.  
  
### <a name="prerequisites"></a>Prérequis  
Avant d’installer SSMA pour les composants de serveur Oracle sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], assurez-vous que le système répond aux exigences suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance est installée. SSMA ne prend pas en charge SQL Server 2008 Express Edition.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 ou une version ultérieure.  
  
-   Le fournisseur de Client Oracle ou le fournisseur OLE DB pour Oracle et la connectivité à la base de données Oracle que vous souhaitez migrer. Vous pouvez installer des fournisseurs à partir du support du produit Oracle ou d’un site Web d’Oracle.  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service Browser doit être en cours d’exécution pendant l’installation. Cela permet de remplir une liste des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’Assistant installation. Vous pouvez désactiver la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service Browser après l’installation.  
  
    > [!NOTE]  
    > Si le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service Browser est en cours d’exécution, mais vous ne voyez toujours pas une liste d’instances dans le programme d’installation, vous devez débloquer le port UDP 1434. Vous pouvez utiliser le pare-feu de Windows pour débloquer temporairement le port, ou vous pouvez désactiver temporairement le pare-feu de Windows. Vous devrez peut-être également désactiver temporairement le logiciel antivirus. Veillez à activer le logiciel antivirus et pare-feux après l’installation.  
  
### <a name="installing-the-extension-pack"></a>L’installation du Pack d’Extension  
Vous pouvez installer le pack d’extension à tout moment avant de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Pour installer le pack d’extension, vous devez être un membre de la **sysadmin** sur l’instance de rôle de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Pour installer le pack d’extension**  
  
1.  Si vous ne le n'avez pas déjà fait, extrayez tous les fichiers à partir du fichier Zip de SSMA.  
  
    Selon la version de WinZip vous disposez, vous pouvez double-cliquez sur le fichier, ou cliquez sur le fichier et sélectionnez **extraire tout** ou **ouvrir dans WinZip**. Suivez les instructions dans l’interface utilisateur de WinZip pour extraire les fichiers.  
  
2.  Copiez SSMA pour Oracle le Pack d’Extension. *n*. Install.exe, où *n* est le numéro de build, à l’ordinateur qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Double-cliquez sur SSMA pour Oracle le Pack d’Extension. *n*. Install.exe.  
  
4.  Dans la page d’accueil, cliquez sur **suivant**.  
  
5.  Dans la page Contrat de licence utilisateur final, lisez le contrat de licence. Si vous acceptez, cochez la **J’accepte les termes du contrat de licence** case à cocher, puis cliquez sur **suivant**.  
  
6.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
7.  Dans la page Prêt pour l’installation, cliquez sur **installer**.  
  
8.  Dans la page de la première étape d’Installation terminé, cliquez sur **suivant**.  
  
    Une boîte de dialogue s’affiche, dans laquelle vous sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’installation de pack d’extension.  
  
9. Sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vous devez migrer les schémas Oracle et puis cliquez sur **suivant**.  
  
    L’instance par défaut a le même nom que l’ordinateur. Instances nommées seront suivis par une barre oblique inverse et le nom d’instance.  
  
10. Dans la page de connexion, sélectionnez la méthode d’authentification, puis cliquez **suivant**.  
  
    L’authentification Windows utilisera vos informations d’identification Windows pour tenter de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom de connexion et mot de passe.  
  
11. Sur la page suivante, sélectionnez **installer d’utilitaires de base de données** *n*, où *n* est le numéro de version, puis cliquez sur **suivant**.  
  
    Le **sysdb** base de données est créée et les procédures stockées et fonctions définies par l’utilisateur sont créés dans cette base de données.  
  
    Si **installer la base de données testeur** activée le testeur **ssmatesterdb** base de données sera créée.  
  
12. Pour installer les utilitaires vers une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sélectionnez **Oui**, puis cliquez sur **suivant**. Ou, pour quitter l’Assistant, cliquez sur **non**.  
  
13. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l’aide de l’utilitaire sqlcmd, exécutez le script suivant pour activer le CLR :  
  
    ```  
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```  
    Si le CLR n’est pas activé, vous recevrez l’erreur suivante quand SSMA se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    SSMA n’a pas pu récupérer les informations de version extension pack assembly. Réinstaller le pack d’extension sur le serveur de base de données.  
  
### <a name="sql-server-database-objects"></a>Objets de base de données SQL Server  
Après avoir installé le pack d’extension, vous allez un, consultez un **ssma_oracle.bcp_migration_packages** table, une **ssma_oracle.db_storage** table et un **ssma_oracle.db_error_list** de table dans le **sysdb** base de données. Vous verrez également plusieurs procédures stockées et fonctions définies par l’utilisateur dans le **ssma_oracle** schéma.  
  
Chaque fois que vous migrez des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA crée un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travail de l’Agent. Ces tâches sont nommées **le package de migration de données ssma_oracle {GUID}** et sont visibles dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nœud de l’Agent de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans le dossier Jobs.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Oracle Client &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
