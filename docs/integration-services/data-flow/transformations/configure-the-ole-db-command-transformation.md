---
title: "Configurer la transformation de commande OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres [Integration Services]"
  - "transformation de commande OLE DB"
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Configurer la transformation de commande OLE DB
  Pour ajouter et configurer une transformation de commande OLE DB, le package doit déjà contenir au moins une tâche de flux de données et une source telle qu'une source de fichier plat ou une source OLE DB. Cette transformation est en général utilisée pour l'exécution de requêtes paramétrables.  
  
### Pour configurer la transformation de commande OLE DB  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de données** puis, à partir de la **Boîte à outils**, faites glisser la transformation de commande OLE DB sur la surface de dessin.  
  
4.  Connectez la transformation de commande OLE DB au flux de données en faisant glisser un connecteur (la flèche verte ou rouge) à partir d'une source de données ou d'une transformation précédente vers la transformation de commande OLE DB.  
  
5.  Cliquez avec le bouton droit sur le composant et sélectionnez Modifier ou Afficher l’**éditeur avancé**.  
  
6.  Sous l'onglet **Gestionnaires de connexions** , sélectionnez un gestionnaire de connexions OLE DB dans la liste **Gestionnaires de connexions** . Pour plus d’informations, consultez [OLE DB Connection Manager](../../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Cliquez sur l’onglet **Propriétés du composant**, puis sur les points de suspension **(…)** dans la zone **SqlCommand**.  
  
8.  Dans l’**Éditeur de valeur de chaîne**, tapez l’instruction SQL paramétrable avec un point d’interrogation (?) comme marqueur de paramètre pour chaque paramètre.  
  
9. Cliquez sur **Actualiser**. Quand vous cliquez sur **Actualiser**, la transformation crée une colonne pour chaque paramètre de la collection Colonnes externes et définit la propriété DBParamInfoFlags.  
  
10. Cliquez sur l'onglet **Propriétés d'entrée et de sortie** .  
  
11. Développez **Entrée de commande OLE DB**, puis **Colonnes externes**.  
  
12. Vérifiez que **Colonnes externes** contient une colonne pour chaque paramètre de l'instruction SQL. Les noms des colonnes sont **Param_0**, **Param_1** et ainsi de suite.  
  
     Vous ne devez pas modifier les noms des colonnes. Si vous modifiez les noms des colonnes, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] génère une erreur de validation pour la transformation de commande OLE DB.  
  
     De même, vous ne devez pas modifier le type de données. La propriété DataType de chaque colonne est définie avec le type de données correct.  
  
13. Si **Colonnes externes** ne répertorie aucune colonne, vous devez les ajouter manuellement.  
  
    -   Cliquez une fois sur **Ajouter une colonne** pour chaque paramètre de l'instruction SQL.  
  
    -   Mettez à jour les noms des colonnes comme suit : **Param_0**, **Param_1** et ainsi de suite.  
  
    -   Spécifiez une valeur dans la propriété DBParamInfoFlags. La valeur doit correspondre à une valeur de l'énumération OLE DB DBPARAMFLAGSENUM. Pour plus d'informations, consultez la documentation de référence OLE DB.  
  
    -   Spécifiez le type de données de la colonne et, en fonction du type de données, spécifiez la page de codes, la longueur, la précision et l'échelle de la colonne.  
  
    -   Pour supprimer un paramètre inutilisé, sélectionnez-le dans **Colonnes externes**, puis cliquez sur **Supprimer une colonne**.  
  
    -   Cliquez sur **Mappage de colonnes** et mappez les colonnes de la liste **Colonnes d'entrée disponibles** à des paramètres de la liste **Colonnes de destination disponibles** .  
  
14. Cliquez sur **OK**.  
  
15. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer** dans le menu **Fichier** .  
  
## Voir aussi  
 [Transformation de commande OLE DB](../../../integration-services/data-flow/transformations/ole-db-command-transformation.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Chemins d'accès d'Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [tâche de flux de données](../../../integration-services/control-flow/data-flow-task.md)  
  
  