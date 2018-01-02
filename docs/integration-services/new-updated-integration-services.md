---
title: "Mise à jour - Documentation d’Integration Services pour SQL Server | Microsoft Docs"
description: "Affichez des extraits de contenu mis à jour récemment dans la documentation d’Integration Services pour Microsoft SQL Server."
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
ms.date: 12/02/2017
ms.author: genemi
ms.workload: integration-services
ms.openlocfilehash: 9660fa7239c14c3adc963cc75ceb98de8316734c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>Nouveau et mis à jour récemment : Integration Services pour SQL Server



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
- *Domaine :* &nbsp; **Integration Services pour SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Stocker et récupérer des fichiers sur des partages de fichiers locaux et dans Azure avec SSIS](lift-shift/ssis-azure-files-file-shares.md)
2. [Valider des packages SSIS déployés sur Azure](lift-shift/ssis-azure-validate-packages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Gestionnaire de connexions Hadoop](#TitleNum_1)
2. [Se connecter à des sources de données locales et à des partages de fichiers Azure avec l’authentification Windows](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-hadoop-connection-managerconnection-managerhadoop-connection-managermd"></a>1. &nbsp; [Gestionnaire de connexions Hadoop](connection-manager/hadoop-connection-manager.md)

*Mise à jour : 28/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 65.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2d68f4e884304f1a28045b42b680c15cc6a41ec5 fb2429466ea4d545682975d8dbea47451ce98ec7  (PR=4113  ,  Filename=hadoop-connection-manager.md  ,  Dirpath=docs\integration-services\connection-manager\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



**Se connecter avec l’authentification Kerberos**

Il existe deux options pour configurer l’environnement local pour pouvoir utiliser l’authentification Kerberos avec le Gestionnaire de connexions Hadoop. Vous pouvez choisir l’option qui correspond le mieux à votre situation.
-   Option 1 : [Joindre l’ordinateur SSIS au domaine Kerberos--#kerberos-join-realm)
-   Option 2 : [Activer l’approbation mutuelle entre le domaine Windows et le domaine Kerberos--#kerberos-mutual-trust)

**<a name="kerberos-join-realm"></a>Option 1 : Joindre l’ordinateur SSIS au domaine Kerberos**


**Exigences :**


-   L’ordinateur servant de passerelle doit se joindre au domaine Kerberos et ne peut se joindre à aucun domaine Windows.

**Configuration :**


**Sur l’ordinateur SSIS :**

1.  Exécutez l’utilitaire **Ksetup** pour configurer le serveur et le domaine du centre de distribution de clés Kerberos.

    L’ordinateur doit être configuré en tant que membre d’un groupe de travail, car un domaine Kerberos est différent d’un domaine Windows. Définissez le domaine Kerberos et ajoutez un serveur de centre de distribution de clés Kerberos, comme indiqué dans l’exemple suivant. Remplacez *REALM.COM* par votre propre domaine.

```
    C:> Ksetup /setdomain REALM.COM`
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
```

    Restart the computer after executing these two commands.

2.  Vérifiez la configuration avec la commande **Ksetup**. Le résultat doit ressembler à l’exemple suivant :

```
    C:> Ksetup
    default realm = REALM.COM (external)
    REALM.com:
        kdc = <your_kdc_server_address>
```

**<a name="kerberos-mutual-trust"></a>Option 2 : Activer l’approbation mutuelle entre le domaine Windows et le domaine Kerberos**


**Exigences :**

-   L’ordinateur servant de passerelle doit se joindre à un domaine Windows.
-   Vous devez avoir l’autorisation de mettre à jour les paramètres du contrôleur de domaine.

**Configuration :**


> [!NOTE]
> Remplacez REALM.COM et AD.COM dans ce didacticiel par votre propre domaine et votre propre contrôleur de domaine.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authenticationlift-shiftssis-azure-connect-with-windows-authmd"></a>2. &nbsp; [Se connecter à des sources de données locales et à des partages de fichiers Azure avec l’authentification Windows](lift-shift/ssis-azure-connect-with-windows-auth.md)

*Mise à jour : 27/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_1))

<!-- Source markdown line 66.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 673386fca53cb60b983e0cb3cd4b9e2ee1dee0de 65458b4dceb92d01184c5e9c6f68ec0e8f16ba08  (PR=4104  ,  Filename=ssis-azure-connect-with-windows-auth.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=19e1c4067142d33e8485cb903a7a9beb7d894015) -->



**Se connecter à un serveur SQL Server local**

Pour vérifier si vous pouvez vous connecter à une instance SQL Server locale, effectuez les actions suivantes :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante pour démarrer SQL Server Management Studio (SSMS) avec les informations d’identification de domaine à utiliser :

```
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
```

3.  À partir de SSMS, vérifiez si vous pouvez vous connecter à l’instance SQL Server locale à utiliser.

**Se connecter à un partage de fichiers local**

Pour vérifier si vous pouvez vous connecter à un partage de fichiers local, effectuez les actions suivantes :

1.  Pour exécuter ce test, recherchez un ordinateur non membre d’un domaine.

2.  Sur l’ordinateur non membre d’un domaine, exécutez la commande suivante. Cette commande ouvre une fenêtre d’invite de commandes avec les informations d’identification de domaine à utiliser. Elle teste ensuite la connectivité au partage de fichiers en obtenant une liste de répertoires.

```
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
```

3.  Vérifiez si la liste de répertoires est retournée pour le partage de fichiers local à utiliser.

**Se connecter à un partage de fichiers sur une machine virtuelle Azure**

Pour vous connecter à un partage de fichiers sur une machine virtuelle Azure, procédez comme suit :

1.  Avec SQL Server Management Studio (SSMS) ou un autre outil, connectez-vous à l’instance SQL Database qui héberge la base de données de catalogues SSIS (SSISDB).

2.  La base de données SSISDB étant la base de données active, ouvrez une fenêtre de requête.

3.  Exécutez la procédure stockée `catalog.set_execution_credential` comme indiqué dans les options suivantes :

```
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
```

**Se connecter à un partage de fichiers dans Azure Files**

Pour plus d’informations sur Azure Files, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 14) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (87 + 0) : **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (5 + 4) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (2 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (10 + 9) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (2 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (4 + 2) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (21 + 0) : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (5 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 0) : **Assistant Migration SQL Server (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


