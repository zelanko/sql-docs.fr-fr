---
title: Mappage de DB2 et les Types de données SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e7e939a8-5e76-4509-beaf-5acd1cab505e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 52322c9b3bf9d7b795458e379f5a8db65fcdbdee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298708"
---
# <a name="mapping-db2-and-sql-server-data-types-db2tosql"></a>Mappage de DB2 et les Types de données SQL Server (DB2ToSQL)
Les types de base de données DB2 diffèrent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de base de données. Lorsque vous convertissez des objets de base de données DB2 à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets, vous devez spécifier le mappage des types de données de DB2 vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez accepter les mappages de type de données par défaut, ou vous pouvez personnaliser les mappages comme indiqué dans les sections suivantes.  
  
## <a name="default-mappings"></a>Mappages par défaut  
SSMA a un ensemble de mappages de types de données par défaut. Pour la liste des mappages par défaut, consultez [paramètres du projet &#40;le mappage de Type&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="type-mapping-inheritance"></a>Type de mappage de l’héritage  
Vous pouvez personnaliser les mappages de type au niveau du projet, niveau de catégorie d’objet (par exemple, toutes les procédures stockées) ou niveau de l’objet. Paramètres sont hérités du niveau supérieur, sauf si elles sont remplacées à un niveau inférieur. Par exemple, si vous mappez **smallmoney** à **money** au niveau du projet, tous les objets dans le projet utilisera ce mappage, sauf si vous personnalisez le mappage au niveau objet ou une catégorie.  
  
Lorsque vous affichez le **le mappage de Type** onglet SSMA, l’arrière-plan est coloré pour afficher lesquelles mappages de type sont héritées. L’arrière-plan d’un mappage de type est jaune pour tout mappage de type hérité, blanc pour tout mappage est spécifié au niveau actuel.  
  
## <a name="customizing-data-type-mappings"></a>Personnalisation mappages de types de données  
La procédure suivante montre comment mapper des types de données sur le projet, la base de données ou le niveau de l’objet :  
  
**Pour mapper les types de données**  
  
1.  Pour personnaliser le mappage de type de données pour la totalité du projet, ouvrez le **paramètres du projet** boîte de dialogue :  
  
    1.  Sur le **outils** menu, sélectionnez **paramètres du projet**.  
  
    2.  Dans le volet gauche, sélectionnez **le mappage de Type**.  
  
        Le graphique de mappage de type et les boutons s’affichent dans le volet droit.  
  
    Ou, pour personnaliser le type de données mise en correspondance à la base de données, table, vue ou niveau de la procédure stockée, sélectionnez la base de données, une catégorie d’objet ou un objet dans l’Explorateur de métadonnées DB2 :  
  
    1.  Dans l’Explorateur de métadonnées de DB2, sélectionnez le dossier ou un objet à personnaliser.  
  
    2.  Dans le volet droit, cliquez sur le **le mappage de Type** onglet.  
  
2.  Pour ajouter un nouveau mappage, procédez comme suit :  
  
    1.  Cliquez sur **Ajouter**.  
  
    2.  Sous **type de Source**, sélectionnez le type de données DB2 à mapper.  
  
    3.  Si le type requiert une longueur, spécifiez la longueur minimale de données pour le mappage dans le **à partir de** boîte et la longueur maximale des données dans le **à** boîte.  
  
        Cela vous permet de personnaliser le mappage de données pour les valeurs inférieures et supérieures du même type de données.  
  
    4.  Sous **type cible**, sélectionnez la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.  
  
        Certains types nécessitent une longueur de type de données cible. Si nécessaire, entrez la nouvelle longueur de données dans le **remplacer par** boîte.  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  Pour modifier un mappage de type de données, procédez comme suit :  
  
    1.  Cliquez sur **Modifier**.  
  
    2.  Sous **type de Source**, sélectionnez le type de données DB2 à mapper.  
  
    3.  Si le type requiert une longueur, spécifiez la longueur minimale de données pour le mappage dans le **à partir de** boîte et la longueur maximale des données dans le **à** boîte.  
  
        Cela vous permet de personnaliser le mappage de données pour les valeurs inférieures et supérieures du même type de données.  
  
    4.  Sous **type cible**, sélectionnez la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.  
  
        Certains types nécessitent une longueur de type de données cible. Si nécessaire, entrez la nouvelle longueur de données dans le **remplacer par** zone, puis [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  Pour supprimer un mappage de type de données personnalisé, procédez comme suit :  
  
    1.  Sélectionnez la ligne dans la liste de mappage de type qui contient le mappage de type de données à supprimer.  
  
    2.  Cliquez sur **Supprimer**.  
  
        Impossible de supprimer les mappages hérités. Toutefois, des mappages hérités sont remplacées par des mappages personnalisés sur un objet spécifique ou une catégorie d’objet.  
  
## <a name="next-steps"></a>Étapes suivantes  
L’étape suivante du processus de migration consiste à [rapport d’évaluation &#40;DB2ToSQL&#41; ](../../ssma/db2/assessment-report-db2tosql.md) ou [conversion des schémas DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md). Si vous créez un rapport d’évaluation, les objets DB2 sont automatiquement convertis durant l’évaluation.  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
