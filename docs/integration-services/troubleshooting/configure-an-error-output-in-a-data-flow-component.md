---
title: "Configurer une sortie d&#39;erreur dans un composant de flux de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "erreurs [Integration Services], composants de flux de données"
  - "composants [Integration Services], flux de données"
  - "erreurs de sortie [Integration Services]"
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Configurer une sortie d&#39;erreur dans un composant de flux de donn&#233;es
  De nombreux composants de flux de données prennent en charge les sorties d’erreur, et en fonction du composant, le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] offre différentes manières de configurer une sortie d’erreur. En plus de configurer une sortie d'erreur, vous pouvez également configurer les colonnes d'une sortie d'erreur. Cela inclut la configuration des colonnes **ErrorCode** et **ErrorColumn** ajoutées par le composant.  
  
## Configuration d'une sortie d'erreur  
 Pour configurer une sortie d'erreur, vous avez deux options :  
  
-   Utilisez la boîte de dialogue **Configurer la sortie d’erreur**. Cette boîte de dialogue vous permet de configurer une sortie d'erreur sur n'importe quel composant de flux de données prenant en charge les sorties d'erreur.  
  
-   Utilisez la boîte de dialogue de l'éditeur pour le composant. Certains composants vous permettent de configurer directement des sorties d'erreur dans la boîte de dialogue de l'éditeur. Toutefois, vous ne pouvez pas configurer des sorties d’erreur dans la boîte de dialogue de l’éditeur pour la source ADO NET, la transformation d’importation de colonne, la transformation de commande OLE DB ou la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Les procédures suivantes décrivent l'utilisation de ces boîtes de dialogue pour configurer des sorties d'erreur.  
  
#### Pour configurer une sortie d'erreur à l'aide de la boîte de dialogue Configurer la sortie d'erreur  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur l’onglet **Flux de données**.  
  
4.  Faites glisser la sortie d'erreur, représentée par la flèche rouge, du composant qui est la source des erreurs vers un autre composant du flux de données.  
  
5.  Dans la boîte de dialogue **Configurer la sortie d’erreur**, sélectionnez une action dans les colonnes **Erreur** et **Troncation** pour chaque colonne de sortie du composant.  
  
6.  Pour enregistrer le package mis à jour, dans le menu **Fichier**, cliquez sur **Enregistrer les éléments sélectionnés**.  
  
#### Pour ajouter une sortie d'erreur à l'aide de la boîte de dialogue de l'éditeur du composant  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur l’onglet **Flux de données**.  
  
4.  Double-cliquez sur les composants de flux de données pour lesquels vous voulez configurer une sortie d'erreur, et en fonction du composant, procédez de l'une des manières suivantes :  
  
    -   Cliquez sur **Configurer la sortie d’erreur**.  
  
    -   Cliquez sur **Sortie d’erreur**.  
  
5.  Définissez l’option **Erreur** pour chaque colonne.  
  
6.  Définissez l’option **Troncation** pour chaque colonne.  
  
7.  Cliquez sur **OK**.  
  
8.  Pour enregistrer le package mis à jour, dans le menu **Fichier**, cliquez sur **Enregistrer les éléments sélectionnés**.  
  
## Configuration des colonnes de sortie d'erreur  
 Pour configurer les colonnes de sortie d’erreur, vous devez utiliser l’onglet **Propriétés d’entrée et de sortie** dans la boîte de dialogue **Éditeur avancé**.  
  
#### Pour configurer des colonnes de sortie d'erreur  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur l’onglet **Flux de données**.  
  
4.  Cliquez avec le bouton droit sur le composant dont vous voulez configurer les colonnes de sortie d’erreur et cliquez sur **Afficher l’éditeur avancé**.  
  
5.  Cliquez sur l’onglet **Propriétés d’entrée et de sortie** et développez **Sortie d’erreur de <nom du composant>\> **puis **Colonnes de sortie**.  
  
6.  Cliquez sur une colonne et mettez à jour ses propriétés.  
  
    > [!NOTE]  
    >  La liste des colonnes comprend les colonnes de l’entrée du composant, les colonnes **ErrorCode** et **ErrorColumn** ajoutées par des sorties d'erreur précédentes et les colonnes **ErrorCode** et **ErrorColumn** ajoutées par ce composant.  
  
7.  Cliquez sur **OK.**  
  
8.  Pour enregistrer le package mis à jour, dans le menu **Fichier**, cliquez sur **Enregistrer les éléments sélectionnés**.  
  
## Voir aussi  
 [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md)  
  
  