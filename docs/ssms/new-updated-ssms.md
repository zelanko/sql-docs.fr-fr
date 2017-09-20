---
title: "Mise à jour - Documentation de SSMS pour SQL Server | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation, pour SQL Server Management Studio (SSMS) pour Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssms-sql-server-management-studio
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 917198902baf85f2bae57c9ade9f8d3e29dea357
ms.contentlocale: fr-fr
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Nouveautés et mises à jour récentes : SQL Server Management Studio (SSMS) pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles existants sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Plage de dates des mises à jour :* &nbsp; **18-07-2017** &nbsp; - au - &nbsp; **11-09-2017**
- *Domaine :* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Fenêtre Sortie dans SQL Server Management Studio](output-window.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Télécharger SQL Server Management Studio (SSMS)](#TitleNum_1)
2. [Se connecter à SQL Server ou Azure SQL Database](#TitleNum_2)
3. [SQL Server Management Studio : journal des modifications (SSMS)](#TitleNum_3)
4. [Créer et mettre à jour les tables de base de données](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1. &nbsp; [Télécharger SQL Server Management Studio (SSMS)](download-sql-server-management-studio-ssms.md)

*Mise à jour : 07/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 63.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 23260f301f86651061b47065bee43d42c92a7be4 0c2178d96b621b96bfcd2fbb782f24792debb407  (PR=2775  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



SSMS 17.2 est la dernière version de SQL Server Management Studio. La génération 17.x de SSMS prend en charge presque tous les composants de SQL Server 2008 à SQL Server 2017. La version 17.x prend également en charge la PaaS SQL Analysis Services.

La version 17.2 inclut :

- L’authentification multifacteur (MFA)
  - L’authentification de plusieurs utilisateurs Azure AD pour une authentification universelle avec l’authentification multifacteur (agent utilisateur avec MFA)
  - Un nouveau champ d’entrée des informations d’identification de l’utilisateur a été ajouté pour l’authentification universelle avec MFA afin de prendre en charge l’authentification de plusieurs utilisateurs.
- La boîte de dialogue de connexion prend désormais en charge les 5 méthodes d’authentification suivantes :
  - Authentification Windows
  - Authentification SQL Server
  - Active Directory - Authentification universelle avec prise en charge de MFA
  - Active Directory - Authentification par mot de passe
  - Active Directory - Authentification intégrée

- L’Assistant Importation/exportation de base de données pour DacFx peut désormais utiliser l’authentification universelle avec MFA.
- Pour la prise en charge de l’API, consultez [IUniversalAuthProvider Interface](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx) (Interface IUniversalAuthProvider).
- La bibliothèque ADAL gérée utilisée par l’authentification universelle Azure AD avec MFA a été mise à niveau vers la version 3.13.9.
- Nouvelle interface CLI prenant en charge le paramètre d’administration Azure AD pour SQL Database et SQL Data Warehouse.

 Pour plus d’informations sur les méthodes d’authentification Active Directory, consultez [Authentification universelle avec SQL Database et SQL Data Warehouse (prise en charge de SSMS pour MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) et [Configurer l’authentification multifacteur Azure SQL Database pour SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La fenêtre Sortie a des entrées pour les requêtes exécutées pendant le développement des nœuds de l’Explorateur d’objets
- Concepteur de vues activé pour les bases de données Azure SQL Database
- Les options de script par défaut pour les objets de script dans l’Explorateur d’objets de SSMS ont changé :



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-a-sql-server-or-azure-sql-databaseobjectconnect-to-an-instance-from-object-explorermd"></a>2. &nbsp; [Se connecter à SQL Server ou Azure SQL Database](object/connect-to-an-instance-from-object-explorer.md)

*Mise à jour : 25/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_1) | [Suivant](#TitleNum_3))

<!-- Source markdown line 40.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cfd72893c35c87df96dc8605807e542be28936e2 840981d3a115a15774a8e47ee2f6a0e5c4177b01  (PR=2961  ,  Filename=connect-to-an-instance-from-object-explorer.md  ,  Dirpath=docs\ssms\object\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



   ![firewall--../media/connect-to-server/new-firewall-rule.png)

1. Pour créer la règle de pare-feu et vous connecter au serveur, cliquez sur **OK**.

1. Le serveur s’affiche dans l’**Explorateur d’objets** après vous être connecté :

   ![connected--../media/connect-to-server/connected.png)

**Étapes suivantes**


[Concevoir, créer et mettre à jour des tables--../visual-db-tools/design-tables-visual-database-tools.md)

**Voir aussi**


[SQL Server Management Studio (SSMS)--../sql-server-management-studio-ssms.md) [Télécharger SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)
[Integration Services](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>3. &nbsp; [SQL Server Management Studio - Journal des modifications (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Mise à jour : 07/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_2) | [Suivant](#TitleNum_4))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1733ce3c556db1e51cb27bf830429f2c42e8f97e 2abb24fd6547e438181039d095cbad027473a57e  (PR=2775  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



Cet article fournit des détails sur les mises à jour, les améliorations et les correctifs de bogues des versions actuelles et précédentes de SSMS. Télécharger [versions précédentes de SSMS ci-dessous--#previous-ssms-releases).

**[SSMS 17.2--download-sql-server-management-studio-ssms.md)**


Disponibilité générale | Numéro de build : 14.0.17177.0

**Améliorations**


- L’authentification multifacteur (MFA)
  - L’authentification de plusieurs utilisateurs Azure AD pour une authentification universelle avec l’authentification multifacteur (agent utilisateur avec MFA)
  - Un nouveau champ d’entrée des informations d’identification de l’utilisateur a été ajouté pour l’authentification universelle avec MFA afin de prendre en charge l’authentification de plusieurs utilisateurs.
- La boîte de dialogue de connexion prend désormais en charge les 5 méthodes d’authentification suivantes :
  - Authentification Windows
  - Authentification SQL Server
  - Active Directory - Authentification universelle avec prise en charge de MFA
  - Active Directory - Authentification par mot de passe
  - Active Directory - Authentification intégrée

- L’Assistant Importation/exportation de base de données pour DacFx utilisant l’authentification universelle avec MFA.
- Pour la prise en charge de l’API, consultez [IUniversalAuthProvider Interface](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx) (Interface IUniversalAuthProvider).
- La bibliothèque ADAL gérée, utilisée par l’authentification universelle Azure AD avec MFA, a été mise à niveau vers la version 3.13.9.
- Par ailleurs, une nouvelle interface CLI a été publiée, prenant en charge le paramètre d’administration Azure AD pour SQL Database et SQL Data Warehouse.

 Pour plus d’informations sur les méthodes d’authentification Active Directory, consultez [Authentification universelle avec SQL Database et SQL Data Warehouse (prise en charge de SSMS pour MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) et [Configurer l’authentification multifacteur Azure SQL Database pour SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La fenêtre Sortie a des entrées pour les requêtes exécutées pendant le développement des nœuds de l’Explorateur d’objets



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-create-and-update-database-tablesvisual-db-toolsdesign-tables-visual-database-toolsmd"></a>4. &nbsp; [Créer et mettre à jour les tables de base de données](visual-db-tools/design-tables-visual-database-tools.md)

*Mise à jour : 25/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_3))

<!-- Source markdown line 30.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f63884ac2d04889e70c505cb5262c8dd81d73ee7 4b4c7aa5e8a0548405f02d11a66b722219fa78f0  (PR=2961  ,  Filename=design-tables-visual-database-tools.md  ,  Dirpath=docs\ssms\visual-db-tools\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



**Créer une table**


1. Cliquez avec le bouton droit sur le nœud **Tables** de votre base de données et sélectionnez **Nouvelle** > **Table** :

    ![Nouvelle table--../media/design-tables/new-table.png)

1. Ajouter [colonnes--column-properties-visual-database-tools.md) à votre table :

    ![concevoir une table--../media/design-tables/new-table2.png)

1. Fermez le concepteur et enregistrez vos modifications.

**Mettre à jour une table**


1. Cliquez avec le bouton droit sur la table sous le nœud **Tables** de votre base de données et sélectionnez **Conception** :

   ![Mettre à jour une table--../media/design-tables/update-table.png)

1. Mettez à jour les paramètres de la table que vous souhaitez :

   ![--../media/design-tables/update-table2.png)

1. Fermez le concepteur et enregistrez vos modifications.

**Voir aussi**


[Tables](http://msdn.microsoft.com/82d7819c-b801-4309-a849-baa63083e83f) [Propriétés de la table &#40;Visual Database Tools&#41;--../../ssms/visual-db-tools/table-properties-visual-database-tools.md) [Propriétés des colonnes--column-properties-visual-database-tools.md) [Ajouter des colonnes à une table--../../relational-databases/tables/add-columns-to-a-table-database-engine.md) [Clés primaire et étrangère--../../relational-databases/tables/primary-and-foreign-key-constraints.md) [Index--../../relational-databases/indexes/indexes.md) [Types de données (Transact-SQL)--../../t-sql/data-types/data-types-transact-sql.md) [Télécharger SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres zones de sujet, dans notre référentiel public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 12) : **Analyse avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (5 + 0) : **Se connecter à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (5 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (19 + 82) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (1 + 8) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (12 + 1) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveau + Mis à jour (0 + 1) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (7 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveau + Mis à jour (1 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveau + Mis à jour (0 + 2) : **SQL Server Migration Assistant (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveau + Mis à jour (1 + 4) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (4 + 1) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)
- [Nouveau + Mis à jour (0 + 1) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveau + Mis à jour (0 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveau + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



