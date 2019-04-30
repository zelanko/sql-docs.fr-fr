---
title: Connexion à MySQL (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to MySQL, MySQL permission
- Connecting to MySQL,reconnecting
ms.assetid: 084c7020-f729-4f91-90e0-143f85fa68d1
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 233b6824ef527a9ed4e7e02164a08e31e41f3699
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253326"
---
# <a name="connecting-to-mysql-mysqltosql"></a>Connexion à MySQL (MySQLToSQL)
Pour migrer des bases de données MySQL vers SQL Server ou SQL Azure, vous devez vous connecter à la base de données MySQL que vous souhaitez migrer. Lorsque vous vous connectez, SSMA Obtient les métadonnées relatives à tous les schémas de MySQL, puis l’affiche dans le volet Explorateur de métadonnées de MySQL. SSMA stocke des informations sur le serveur de base de données, mais ne stocke pas les mots de passe.  
  
Votre connexion à la base de données reste active jusqu'à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez reconnecter si vous souhaitez une connexion active à la base de données.  
  
Métadonnées relatives à la base de données MySQL ne sont pas automatiquement mis à jour. Au lieu de cela, si vous souhaitez mettre à jour les métadonnées dans l’Explorateur de métadonnées MySQL, vous devez manuellement mettre à jour il. Pour plus d’informations, consultez la section « L’actualisation des métadonnées de MySQL » plus loin dans cette rubrique.  
  
## <a name="required-mysql-permissions"></a>Autorisations requises MySQL  
Le compte qui est utilisé pour se connecter à la base de données MySQL doit avoir au moins **CONNECT** autorisations. Cela permet de SSMA obtenir les métadonnées à partir de schémas appartenant à l’utilisateur connecté. Pour obtenir des métadonnées pour les objets dans d’autres schémas, puis de convertir les objets dans ces schémas, le compte doit disposer des autorisations suivantes :  
  
-   'SHOW' des privilèges sur les objets de base de données  
  
-   Privilège 'SELECT' sur 'Information_schema'  
  
-   'SELECT' privilège sur mysql (pour des UDF)  
  
## <a name="establishing-a-connection-to-mysql"></a>L’établissement d’une connexion à MySQL  
Lorsque vous vous connectez à une base de données, SSMA lit les métadonnées de base de données, puis ajoute ces métadonnées au fichier projet. Ces métadonnées sont utilisée par SSMA lorsqu’il convertit des objets à la syntaxe SQL Server ou SQL Azure, et lorsqu’il migre les données vers SQL Server ou SQL Azure. Vous pouvez parcourir ces métadonnées dans le volet Explorateur de métadonnées de MySQL et passez en revue les propriétés des objets de base de données individuelle.  
  
> [!IMPORTANT]  
> Avant d’essayer de vous connecter, vérifiez que le serveur de base de données est en cours d’exécution et qu’il peut accepter les connexions.  
  
**Pour vous connecter à MySQL**  
  
1.  Sur le **fichier** menu, sélectionnez **se connecter à MySQL** (cette option est activée après la création du projet).  
  
    Si vous êtes déjà connecté à MySQL, le nom de la commande sera **reconnexion à MySQL**.  
  
2.  Dans le **fournisseur** , sélectionnez le pilote de 5.1 ODBC MySQL (approuvé). Il est le fournisseur par défaut en mode standard.  
  
3.  Dans le **Mode** boîte, sélectionnez **mode Standard**. Il s'agit du mode par défaut.  
  
    Utiliser le mode standard pour spécifier le nom du serveur et le port.  
  
4.  Dans **mode Standard**, indiquez les valeurs suivantes :  
  
    1.  Dans le **nom du serveur** , entrez le nom du serveur MySQL. Dans le **port du serveur** , entrez le numéro de port pour être 3306. Il est le port par défaut.  
  
    2.  Dans le **nom d’utilisateur** , entrez un compte de MySQL qui dispose des autorisations nécessaires.  
  
    3.  Dans le **mot de passe** , entrez le mot de passe pour le nom d’utilisateur spécifié.  
  
5.  **SSL :** Si vous souhaitez vous connecter en toute sécurité à MySQL, servez-vous de Socket couche SSL (Secure) en vérifiant la **SSL** case à cocher.  
  
6.  **Configurer :** Il fournit une option pour configurer la connexion à MySQL via couche SSL (Secure Socket).  
  
    > [!NOTE]  
    > Pour activer **configurer**, SSL doit être défini sur **True**.  
  
    Lorsque vous cliquez sur le bouton « Configurer », une boîte de dialogue s’affiche. Pour utiliser le chiffrement alors que la connexion à la base de données MySQL, chemin d’accès aux fichiers de trois certificat suivants présents dans la boîte de dialogue doit être défini [confidentialité améliorée messagerie certificats (PEM)] :  
  
    -   **Autorité de certification SSL :** Spécifie le chemin d’accès à un fichier avec une liste d’approbation autorités de certification SSL.  
  
    -   **Certificat SSL :** Spécifie le nom du fichier de certificat SSL à utiliser pour établir une connexion sécurisée.  
  
    -   **CLÉ SSL :** Spécifie le nom du fichier de clé SSL à utiliser pour établir une connexion sécurisée.  
  
    > [!NOTE]  
    > -   Le **OK** bouton est activé lorsque les informations requises ont été fournies. Si un des chemins de fichier ne sont pas valide, le bouton « OK » reste désactivé.  
    > -   Le **Annuler** bouton ferme la boîte de dialogue et **désactive** l’option SSL à partir du formulaire de connexion principale.  
  
7.  Pour plus d’informations, consultez [se connecter à MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
## <a name="reconnecting-to-mysql"></a>Rétablir la connexion à MySQL  
Votre connexion au serveur de base de données reste active jusqu'à ce que vous fermiez le projet. Lorsque vous rouvrez le projet, vous devez reconnecter si vous souhaitez une connexion active à la base de données. Vous pouvez travailler hors connexion jusqu'à ce que vous souhaitez mettre à jour des métadonnées, charger des objets de base de données dans SQL Server ou SQL Azure et migrer des données.  
  
## <a name="refreshing-mysql-metadata"></a>L’actualisation des métadonnées de MySQL  
Métadonnées relatives à la base de données MySQL ne sont pas actualisée automatiquement. Les métadonnées dans l’Explorateur de métadonnées MySQL sont un instantané de métadonnées lors de la première connexion, ou la dernière fois que vous avez actualisé manuellement les métadonnées. Vous pouvez manuellement mettre à jour des métadonnées pour tous les schémas, un seul schéma ou les objets de base de données individuelle.  
  
**Pour actualiser les métadonnées**  
  
1.  Assurez-vous que vous êtes connecté à la base de données.  
  
2.  Dans l’Explorateur de métadonnées de MySQL, sélectionnez la case à cocher en regard de chaque objet de schéma ou de base de données que vous souhaitez mettre à jour.  
  
3.  Avec le bouton droit **schémas**, ou le schéma individuel ou une base de données de l’objet, puis sélectionnez **Actualiser à partir de la base de données**.  
  
    Si vous n’avez pas d’une connexion active, SSMA affichera le **se connecter à MySQL** boîte de dialogue afin de pouvoir vous connecter.  
  
4.  Dans l’actualisation à partir de la boîte de dialogue base de données, définir les objets à actualiser.  
  
    -   Pour actualiser un objet, cliquez sur le **Active** champ en regard de l’objet jusqu'à ce qu’une flèche apparaît.  
  
    -   Pour éviter un objet en cours d’actualisation, cliquez sur le **Active** champ adjacent à l’objet jusqu'à un **X** s’affiche.  
  
    -   Pour actualiser ou refuser une catégorie d’objets, cliquez sur le **Active** champ adjacent dans le dossier de catégorie.  
  
    -   Pour afficher les définitions de codage en couleurs, cliquez sur le **légende** bouton.  
  
5.  Cliquez sur **OK**.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration est [connexion à SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de MySQL vers SQL Server - Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
