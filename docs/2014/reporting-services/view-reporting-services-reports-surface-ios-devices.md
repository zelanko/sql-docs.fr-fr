---
title: Afficher des rapports d’Reporting Services sur des appareils Microsoft surface et Apple iOS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5ca879d51f947ec078b3c1b7e14842ea926f0240
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78174848"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Afficher des rapports Reporting Services sur des appareils Microsoft Surface et Apple iOS
  Cet article décrit les fonctionnalités et les flux de travail de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pris en charge pour les appareils Microsoft Surface ainsi que les appareils utilisant Apple iOS 6 et Apple Safari, tels que les iPad.

## <a name="view-and-interact-with-reports"></a>Afficher et interagir avec les rapports
 À compter de [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge l'affichage et l'interactivité de base sur les appareils Microsoft Surface et les appareils utilisant Apple iOS et le navigateur Apple Safari, tels que les iPad. Vous pouvez également publier des rapports à l'aide d'appareils Microsoft Surface.

 ![Bureau](media/videothumbnail.jpg "Bureau IPad") de l’iPad Regardez une démonstration de l’affichage des rapports sur un iPad.

 Vous pouvez également afficher des rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur un appareil Windows Phone 8.

 Pour utiliser les fonctionnalités décrites dans cette rubrique, installez l'un des éléments suivants :

-   Pour un serveur de rapports en mode natif, installez [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] ou version ultérieure.

     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]peut être téléchargé à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=35575).

-   Pour un serveur de rapports en mode SharePoint, installez [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] ou version ultérieure du complément de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint.

 **Pour afficher un rapport et interagir avec sur votre iPad ou votre appareil Microsoft Surface**

1.  Vérifiez que vous pouvez vous connecter au serveur de rapports ou au site SharePoint où réside le rapport.

2.  Ouvrez le rapport en effectuant une des actions suivantes.

    -   **Démarrer à partir d’un message électronique :** À partir d’un message électronique créé par [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] un abonnement, appuyez sur l’URL du rapport. Le rapport s'ouvre dans le navigateur.

    -   **Démarrer à partir du serveur de rapports :** Parcourez le répertoire [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur le serveur de rapports, puis appuyez sur le nom du rapport pour ouvrir le rapport.

    -   **Démarrer à partir d’une bibliothèque de documents SharePoint :** Accédez à une bibliothèque de documents SharePoint qui [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] contient des rapports, puis appuyez sur le nom du rapport. Vous pouvez afficher et interagir avec le rapport.

        > [!IMPORTANT]
        >  Pour un iPad, assurez-vous que la propriété **Private Browsing** de Safari est désactivée.

    -   **Composant WebPart SharePoint :** Si le composant WebPart a été ajouté à une page SharePoint, vous pouvez [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] afficher des rapports.

3.  Sur votre appareil Microsoft Surface, vous pouvez également ouvrir le rapport grâce au Gestionnaire de rapports. Parcourez le répertoire du Gestionnaire de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , puis touchez le nom du rapport pour l'ouvrir.

    > [!IMPORTANT]
    >  L'affichage des rapports dans le Gestionnaire de rapports n'est pas pris en charge sur un iPad.

4.  Faites défiler le rapport et zoomez en procédant comme suit.

    -   Pour faire défiler le rapport, faites glisser votre doigt sur l'écran (vers le haut, vers le bas, à gauche ou à droite). Il s'agit du mouvement de balayage.

    -   Pour effectuer un zoom avant, placez deux doigts sur l'écran et séparez-les. Pour effectuer un zoom arrière, placez deux doigts sur l'écran et rapprochez-les. Il s'agit du mouvement de pincement.

5.  Parcourez le rapport et interagissez avec lui en procédant comme suit.

    -   Réduisez et développez les éléments du rapport, les lignes et les colonnes associées à des groupes, en touchant le signe plus (+) pour réduire et le signe moins (-) pour développer.

    -   Inversez l'ordre croissant et décroissant des lignes dans une table ou des lignes et des colonnes dans une matrice, en touchant le bouton de tri. Le bouton de tri est généralement situé dans l'en-tête de colonne.

    -   Développez et réduisez le volet des paramètres, en touchant le bouton fléché en haut du rapport.

    -   Sélectionnez une valeur de paramètre en touchant la zone ou le contrôle en regard du paramètre. Touchez **Afficher le rapport** pour appliquer la valeur de paramètre au rapport.

    -   Recherchez le contenu du rapport en touchant la case à cocher située en regard de **Rechercher**, entrez un terme de recherche, puis touchez **Rechercher**.

    -   Parcourez les pages du rapport en touchant les boutons de navigation, ou en touchant la zone de texte en regard des boutons et en tapant le numéro de page.

    -   Accédez aux URL en touchant les liens hypertexte qui ont été ajoutés aux éléments du rapport, tels que les zones de texte, les images, les graphiques, les jauges.

    -   Exportez le rapport en touchant l'icône du **menu déroulant Exporter** , puis en touchant un format de fichier.

        -   Si vous affichez le rapport sur un appareil Microsoft surface, vous pouvez exporter le rapport dans l’un des formats suivants.

            -   Fichier XML avec données de rapport

            -   CSV (délimité par des virgules)

            -   PDF

            -   MHTML (archive Web)

            -   Excel

            -   TIFF

            -   Word

        -   Si vous affichez le rapport sur un iPad, vous pouvez exporter le rapport en tant que fichier TIFF ou PDF.

## <a name="authentication"></a>Authentication
 L'authentification RSWindowsNTLM et l'authentification RSWindowsBasic fonctionnent avec [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif et avec l'iPad.

 En général, il est recommandé de ne pas utiliser RSWindowsBasic dans un environnement autre que https car ce type d'authentification ne garantit pas la confidentialité des informations de connexion transmises.

 Pour plus d'informations sur l'authentification RSWindowsNTLM et RSWindowsBasic, consultez [Authentication with the Report Server](security/authentication-with-the-report-server.md).

## <a name="uploading-reports"></a>Téléchargement de rapports
 Publiez des rapports à partir d'un appareil Microsoft Surface à l'aide des méthodes suivantes, si vous disposez des autorisations appropriées.

> [!IMPORTANT]
>  Ces méthodes ne sont pas prises en charge sur un iPad.

-   Téléchargez un fichier de définition de rapport (.rdl) dans une bibliothèque de documents SharePoint en ouvrant la bibliothèque et en touchant **Télécharger un document**.

-   Téléchargez un fichier de définition de rapport dans la base de données du serveur de rapports en ouvrant le Gestionnaire de rapports et en touchant **Télécharger un fichier**.

## <a name="additional-information"></a>Informations supplémentaires
 Pour plus d'informations sur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et les navigateurs pris en charge, consultez :

-   [Planification de la prise en charge des navigateurs Reporting Services et Power View &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)

 Pour plus d'informations sur Microsoft Business Intelligence et les appareils mobiles, consultez les rubriques suivantes :

-   [Vue d’ensemble des appareils mobiles et SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).

-   [Navigateurs d’appareils mobiles pris en charge dans SharePoint 2013](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).

-   [Affichage des rapports et des tableaux de bord sur les appareils Apple iPad (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).

-   [Affichage des rapports de Reporting Services sur un iPad (vidéo)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).

-   [Affichage de rapports Reporting Services sur un appareil Microsoft Surface RT (vidéo)](https://technet.microsoft.com/sqlserver/dn146017)


