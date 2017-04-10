---
title: "Comparer des tables r&#233;pliqu&#233;es pour identifier les diff&#233;rences (programmation de r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "tablediff (utilitaire)"
  - "comparaison des tables répliquées"
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Comparer des tables r&#233;pliqu&#233;es pour identifier les diff&#233;rences (programmation de r&#233;plication)
  La validation d'article est utilisée pour déterminer si les données publiées pour les articles de table sur le serveur de publication et sur l'Abonné ne sont pas identiques, ce qui peut indiquer une non-convergence. Pour plus d’informations, consultez [valider les données répliquées](../../../relational-databases/replication/validate-replicated-data.md). Toutefois, la validation retourne uniquement des informations de succès ou d'échec et ne fournit pas d'informations sur les différences entre les tables sources et les tables cibles. Le **tablediff** retourne utilitaire de ligne de commande détaillées sur les différences entre deux tables d’informations et peut même générer un [!INCLUDE[tsql](../../../includes/tsql-md.md)] script pour l’abonnement en convergence avec les données du serveur de publication.  
  
> [!NOTE]  
>  Le **tablediff** utilitaire est uniquement pris en charge pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] serveurs.  
  
### Pour comparer les différences des tables répliquées à l'aide de tablediff  
  
1.  À partir de l’invite de commandes n’importe quel serveur dans une topologie de réplication, exécutez la [utilitaire tablediff](../../../tools/tablediff-utility.md). Spécifiez les paramètres suivants :  
  
    -   **-sourceserver** - nom du serveur sur lequel les données sont connues soit correct, généralement le serveur de publication.  
  
    -   **-sourcedatabase** - nom de la base de données contenant les données correctes.  
  
    -   **-sourcetable** - nom de la table source pour l’article en cours de comparaison.  
  
    -   (Facultatif) **-sourceschema** -propriétaire du schéma de la table source, si ce n’est pas le schéma par défaut.  
  
    -   (Facultatif) **-sourceuser** et **- sourcepassword** lors de l’utilisation de l’authentification SQL Server pour se connecter au serveur de publication.  
  
        > [!IMPORTANT]  
        >  Lorsque c'est possible, utilisez l'authentification Windows. Si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], invitez les utilisateurs à entrer les informations d'identification de sécurité pendant l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
    -   **-destinationserver** - nom du serveur sur lequel les données sont comparées, habituellement un abonné.  
  
    -   **-destinationdatabase** - nom d’une la base de données en cours de comparaison.  
  
    -   **-destinationtable** - nom de la table en cours de comparaison.  
  
    -   (Facultatif) **-destinationschema** -propriétaire du schéma de la table de destination, si ce n’est pas le schéma par défaut.  
  
    -   (Facultatif) **-destinationuser** et **- destinationpassword** lors de l’utilisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’authentification pour se connecter à l’abonné.  
  
        > [!IMPORTANT]  
        >  Lorsque c'est possible, utilisez l'authentification Windows. Si vous devez utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], invitez les utilisateurs à entrer les informations d'identification de sécurité pendant l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
    -   (Facultatif) Utilisez **- c** pour effectuer une comparaison au niveau des colonnes.  
  
    -   (Facultatif) Utilisez **- q** pour faire rapidement, ligne comparaison count - et schéma uniquement.  
  
    -   (Facultatif) Spécifiez un nom de fichier et le chemin d’accès pour **-o** pour enregistrer les résultats dans un fichier.  
  
    -   (Facultatif) Spécifier une table dans la base de données d’abonnement dans lequel insérer les résultats de **et -**. Si la table existe déjà, spécifiez **-dt** tout d’abord supprimer la table.  
  
    -   (Facultatif) Utilisez **-f** pour générer un [!INCLUDE[tsql](../../../includes/tsql-md.md)] fichier et corriger les données sur l’abonné afin qu’elles correspondent à celles du serveur de publication. Utilisez **-df** pour spécifier le nombre de [!INCLUDE[tsql](../../../includes/tsql-md.md)] instructions dans chaque fichier.  
  
    -   (Facultatif) Utilisez **-rc** et **-ri** pour spécifier le nombre de tentatives pour relancer une opération et l’intervalle de nouvelle tentative.  
  
    -   (Facultatif) Utilisez **-strict** pour appliquer la comparaison stricte de schéma entre les tables source et de destination.  
  
## Voir aussi  
 [Valider des données sur l'Abonné](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  