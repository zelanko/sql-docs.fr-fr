---
title: Mappage de schémas DB2 à des schémas de SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 50845a9bdf3c3185d7b69bb86a75b2a3d332ef6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074172"
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>Mappage de schémas DB2 à des schémas de SQL Server (DB2ToSQL)
Dans DB2, chaque base de données contient un ou plusieurs schémas. Par défaut, SSMA migre tous les objets d’un schéma DB2 vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une base de données nommée pour le schéma. Toutefois, vous pouvez personnaliser le mappage entre les schémas DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les bases de données.  
  
## <a name="db2-and-sql-server-schemas"></a>Schémas DB2 et SQL Server  
Une base de données DB2 contient des schémas. Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient plusieurs bases de données, chacune pouvant avoir plusieurs schémas.  
  
Le concept DB2 d’un schéma est mappé au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concept d’une base de données et à l’un de ses schémas. Par exemple, DB2 peut avoir un schéma nommé **HR**. Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut avoir une base de données nommée **HR**et au sein de cette base de données sont des schémas. Un schéma est le schéma **dbo** (ou propriétaire de la base de données). Par défaut, le schéma DB2 **HR** est mappé à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données et au schéma **hr. dbo**. SSMA fait référence à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la combinaison base de données et schéma en tant que schéma.  
  
Vous pouvez modifier le mappage entre DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les schémas.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données et du schéma cibles  
Dans SSMA, vous pouvez mapper un schéma DB2 à n’importe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quel schéma disponible.  
  
**Pour modifier la base de données et le schéma**  
  
1.  Dans l’Explorateur de métadonnées DB2, sélectionnez **schémas**.  
  
    L’onglet **mappage de schéma** est également disponible lorsque vous sélectionnez une base de données individuelle, le dossier **schémas** ou des schémas individuels. La liste de l’onglet **mappage de schéma** est personnalisée pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur l’onglet **mappage de schéma** .  
  
    Vous verrez une liste de tous les schémas DB2, suivis d’une valeur cible. Cette cible est indiquée dans une notation en deux parties (*Database. Schema*) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vos objets et vos données seront migrés.  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez modifier, puis cliquez sur **modifier**.  
  
    Dans la boîte de dialogue **choisir un schéma cible** , vous pouvez rechercher le schéma et la base de données cible disponibles, ou taper le nom de la base de données et du schéma dans la zone de texte en deux parties (Database. Schema), puis cliquer sur **OK**.  
  
4.  Les modifications apportées à la cible sous l’onglet **mappage de schéma** .  
  
**Modes de mappage**  
  
-   Mappage à SQL Server  
  
Vous pouvez mapper une base de données source à une base de données cible. Par défaut, la base de données source est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mappée à la base de données cible avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible mappée n’est pas existante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sur, vous êtes invité à entrer un message **«la base de données et/ou le schéma n’existe pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les métadonnées cibles. Il serait créé au cours de la synchronisation. Voulez-vous continuer ?»** Cliquez sur Oui. De même, vous pouvez mapper le schéma à un schéma non existant sous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la base de données cible, qui sera créé lors de la synchronisation.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Rétablissement de la base de données et du schéma par défaut  
Si vous personnalisez le mappage entre un schéma DB2 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un schéma, vous pouvez rétablir les valeurs par défaut du mappage.  
  
**Pour rétablir la base de données et le schéma par défaut**  
  
1.  Sous l’onglet Mappage de schéma, sélectionnez n’importe quelle ligne et cliquez sur **rétablir les valeurs par défaut** pour rétablir la base de données et le schéma par défaut.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez analyser la conversion d’objets DB2 en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets, vous pouvez effectuer un rapport de migration des [données (SSMA commun)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241).  
  
## <a name="see-also"></a>Voir aussi  
[Connexion à SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[Migration de bases de données DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
