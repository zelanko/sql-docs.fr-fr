---
title: Trace (Client d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tracer
- connections
ms.assetid: 4aea3e17-cd0f-48dd-8f22-b54a6c716426
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee0268eb960aab09029774b6ad26ccccd3d352e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326519"
---
# <a name="trace-data-mining-client-for-excel"></a>Trace (Client d'exploration de données pour Excel)
  ![Bouton trace](media/misc-trace.gif "bouton Trace")  
  
 Le **suivi** boîte de dialogue vous permet de surveiller les instructions sont envoyées à l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que vous utilisez pour l’exploration de données. Une fois que vous avez créé une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], toutes les interactions entre le client et le serveur sont enregistrées le **suivi** volet, y compris les instructions qui créent des structures, ajouter les modèles d’exploration de données et des prédictions, ainsi que certains messages retournés à partir du serveur.  
  
 Selon l'action demandée, l'instruction peut être une requête de définition de données DMX (Data Mining Extensions) ou une requête de manipulation de données, un paquet ASSL (Analysis Services Scripting Language) ou un appel à une procédure stockée Analysis Services. Toutefois, les valeurs de données et les résultats numériques réels ne sont pas affichés.  
  
 **Trace** surveille uniquement la connexion actuelle et le contenu de la **suivi** boîte de dialogue ne sont pas stockées.  
  
## <a name="options"></a>Options  
 Volet de suivi de l'exploration de données  
 Répertorie toutes les instructions envoyées du client Excel vers le serveur.  
  
 Selon l'action demandée, l'instruction peut être une manipulation de données DMX, une instruction de définition de données, un appel à une procédure stockée Analysis Service ou un paquet XML/A.  
  
 **Connexion en cours**  
 Cliquez sur cette option pour afficher la définition de la connexion active. La définition inclut le nom de la connexion, le fournisseur, la source de données, le catalogue, l'heure à laquelle la connexion a été utilisée pour la dernière fois dans le cadre d'une transaction, ainsi que l'état actuel (Ouvert, Inactif).  
  
 **Utiliser les modèles de session**  
 Activez cette case à cocher pour stocker les modèles et les structures d'exploration de données en tant qu'objets temporaires sur le serveur. Les modèles et structures que vous créez seront uniquement disponibles pendant la durée de la session actuelle.  
  
 Désélectionnez cette option pour enregistrer vos modèles ou structures en les stockant sur un serveur Analysis Services.  
  
 **Remarque** la possibilité d’utiliser des objets temporaires est disponible uniquement lorsque vous utilisez les outils d’analyse de Table pour Excel. Les modèles d'exploration de données Visio et le Client d'exploration de données pour Excel nécessitent le stockage des structures et des modèles sur le serveur.  
  
## <a name="tracing-temporary-structures-and-models"></a>Traçage des structures et modèles temporaires  
 Si vous utilisez les Outils d'analyse de table, lesquels créent par défaut des modèles et structures temporaires, l'activité entre le serveur et le client est surveillée, mais les modèles ou les structures que vous créez ne sont pas enregistrés de façon permanente sur le serveur.  
  
 Si vous souhaitez conserver votre travail lorsque l’un des outils d’analyse de Table, vous pouvez désélectionner l’option, **utiliser des modèles de session**, pour être enregistrées de manière permanente sur le serveur de vos modèles. Vous pouvez également copier les instructions figurant dans le **suivi** volet dans un fichier afin que vous pouvez recréer votre travail plus tard.  
  
## <a name="understanding-sessions"></a>Description des sessions  
 Lorsque vous vous connectez à une instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le complément d'exploration de données lance une session. Chaque session reçoit un identificateur de session qui identifie une session existante sur l'instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cependant, un identificateur de session ne garantit pas qu'une session reste valide. La session peut expirer si son délai d'expiration est écoulé ou si la connexion associée à la session est déconnectée. Si la session expire et n'est plus valide, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] termine la session et restaure toutes les transactions qui sont en cours. Si un message est envoyé avec un identificateur de session qui n'est plus valide, le message échoue et génère une erreur indiquant que la session spécifiée est introuvable.  
  
 Bien que certains modèles d'exploration de données soient explicitement stockés sur le serveur, ce n'est pas le cas des modèles et structures d'exploration de données de session, et aucun enregistrement de l'activité de l'exploration de données de session n'est conservé. Étant donné que les modèles et structures d'exploration de données temporaires sont supprimés dès que vous mettez fin à la session, vous devez éviter de fermer votre classeur Excel tant que vous n'avez pas enregistré le travail que vous souhaitez conserver.  
  
## <a name="changing-connections"></a>Modification des connexions  
 Les modifications apportées aux connexions ne suppriment pas les traces des connexions précédentes. Seule la fermeture du classeur efface la session.  
  
 Si vous modifiez les connexions tout en travaillant dans un classeur Excel, la modification des connexions n’est pas enregistrée dans le **suivi** volet. Pour afficher explicitement le nom et l’état de la connexion actuelle, vous devez cliquer sur **connexion actuelle**.  
  
## <a name="understanding-statements-in-the-tracer"></a>Présentation des instructions du volet Tracer  
 Le langage DMX vous permet de créer et d'utiliser des modèles d'exploration de données dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Vous pouvez utiliser le langage DMX pour créer la structure de nouveaux modèles d'exploration de données, pour effectuer l'apprentissage de ces modèles ainsi que pour les parcourir, les gérer et effectuer des prédictions. Le langage DMX se compose d'instructions DDL (langage de définition de données), d'instructions DML (langage de manipulation de données), de fonctions et d'opérateurs.  
  
 Toutefois, cette rubrique n'a pas pour objectif de traiter de manière approfondie les instructions DMX et leur syntaxe. Toutefois, vous pouvez utiliser les informations contenues dans le **suivi** pour trouver des informations détaillées sur le comportement d’une instruction DMX. Les compléments d'exploration de données pour Excel peuvent également vous permettre de créer des instructions DMX complexes et d'interagir avec un serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Pour plus d’informations, consultez [requête &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Un grand nombre d'instructions DMX sont paramétrées. Pour les types simples, les valeurs des paramètres sont répertoriées sous l'instruction. Toutefois, pour les types complexes, seul le type de paramètre est répertorié.  
  
 SQL Server Analysis Services utilise également le protocole XMLA (XML for Analysis) pour gérer toutes les communications entre les applications clientes, notamment le Client d'exploration de données pour Excel et une instance d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Pour plus d'informations sur la syntaxe DMX ainsi que sur les commandes et les éléments dans XMLA, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Certaines instructions envoyées au serveur peuvent inclure des requêtes qui appellent des procédures stockées système Analysis Services. Pour plus d’informations, consultez la documentation en ligne de SQL Server.  
  
  
