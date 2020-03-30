---
title: Codage en couleurs dans les éditeurs de requête
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], color coding
- color coding [Query Editor]
ms.assetid: 802882dc-c997-4e3f-8a01-994bb43169ae
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71801d025b8b761adbcd80b8b3a10be92cd5c5ad
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254022"
---
# <a name="color-coding-in-query-editors"></a>Codage en couleurs dans les éditeurs de requête
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Une catégorie est attribuée au texte que vous entrez dans les éditeurs de code. Chaque catégorie est identifiée par une couleur. Les couleurs vous aident rapidement à trouver un texte dans votre code. Par exemple, les commentaires apparaissent en vert sombre. Le tableau suivant répertorie les couleurs les plus courantes. Vous pouvez afficher la liste complète des couleurs et de leur catégorie ainsi que configurer un modèle de couleurs personnalisé à partir du menu **Outils**, **Options** . Pour plus d’informations sur la modification des couleurs par défaut, consultez [Modifier la couleur, la taille et le style de la police](../../relational-databases/scripting/change-font-color-size-and-style.md).  
  
## <a name="default-code-colors"></a>Couleurs du code par défaut  
  
|Couleur|Category|  
|-----------|--------------|  
|Rouge|Chaîne SQL|  
|Vert foncé|Commentaire|  
|Noir avec un arrière-plan argenté|Commande SQLCMD|  
|Magenta|Fonction système|  
|Vert|Table système, vue ou fonction table. Également, les schémas système et INFORMATION_SCHEMA.|  
|Bleu|Mot clé|  
|Bleu-vert|Numéros de lignes ou paramètre de modèle|  
|Rouge foncé|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procédure stockée|  
|Gris foncé|Opérateurs|  
  
## <a name="status-bar"></a>Barre d’état  
 Vous pouvez configurer les serveurs inscrits ou les serveurs du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans l'Explorateur d'objets pour avoir des couleurs différentes dans la barre d'état de l'Éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Cela vous permet d'identifier à quel serveur chaque fenêtre d'éditeur est connectée lorsque plusieurs fenêtres sont ouvertes en même temps. Pour plus d’informations sur la définition des couleurs de la barre d’état, consultez [Barre d’état &#40;éditeur de requête du moteur de base de données&#41;](../../relational-databases/scripting/status-bar-database-engine-query-editor.md).  
  
 Certains types d'éditeurs n'affichent pas la barre d'état ou ne prennent pas en charge plusieurs couleurs.  
  
  
