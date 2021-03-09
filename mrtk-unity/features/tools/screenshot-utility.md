---
title: ScreenshotUtility
description: Documentation sur l’utilisation de l’outil de capture d’écran dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: a1f5e6503244852d79abaf143f8e922ceb1b489c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101766261"
---
# <a name="screenshot-utility"></a><span data-ttu-id="00e0b-104">Utilitaire de capture d’écran</span><span class="sxs-lookup"><span data-stu-id="00e0b-104">Screenshot utility</span></span>

<span data-ttu-id="00e0b-105">La prise de captures d’écran dans Unity pour la documentation et les images promotionnelles peut souvent être fastidieuse, et le résultat rarement convaincant.</span><span class="sxs-lookup"><span data-stu-id="00e0b-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="00e0b-106">C’est là que la classe `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) entre en jeu.</span><span class="sxs-lookup"><span data-stu-id="00e0b-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="00e0b-107">La classe ScreenshotUtility vous permet de prendre des captures d’écran via des éléments de menu et des API publiques dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="00e0b-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="00e0b-108">Les captures d’écran peuvent être prises dans différentes résolutions et avec des couleurs claires transparentes pour être utilisées dans la composition simple d’images.</span><span class="sxs-lookup"><span data-stu-id="00e0b-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="00e0b-109">La prise de captures d’écran depuis une build autonome n’est pas prise en charge par cet outil.</span><span class="sxs-lookup"><span data-stu-id="00e0b-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="00e0b-110">Prise de captures d’écran</span><span class="sxs-lookup"><span data-stu-id="00e0b-110">Taking screenshots</span></span>

<span data-ttu-id="00e0b-111">Vous pouvez facilement prendre des captures d’écran dans l’éditeur en sélectionnant *Mixed Reality Toolkit->Utilities->Take Screenshot*, puis l’option souhaitée.</span><span class="sxs-lookup"><span data-stu-id="00e0b-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="00e0b-112">Veillez à ce que l’onglet de la fenêtre de jeu soit visible si vous prenez la capture quand vous ne jouez pas, sinon la capture ne peut pas être enregistrée.</span><span class="sxs-lookup"><span data-stu-id="00e0b-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="00e0b-113">Par défaut, toutes les captures d’écran sont enregistrées dans le [chemin du cache temporaire](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), le chemin de la capture s’affichera dans la console Unity.</span><span class="sxs-lookup"><span data-stu-id="00e0b-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![Élément de menu de l’utilitaire de capture d’écran](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="00e0b-115">Exemple de prise de capture d’écran</span><span class="sxs-lookup"><span data-stu-id="00e0b-115">Example screenshot capture</span></span>

<span data-ttu-id="00e0b-116">La capture d’écran ci-dessous a été prise avec l’option *"4x Resolution (Transparent Background)"* .</span><span class="sxs-lookup"><span data-stu-id="00e0b-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="00e0b-117">Le résultat est une image haute résolution avec les pixels normalement représentés par la couleur claire enregistrée comme pixels transparents.</span><span class="sxs-lookup"><span data-stu-id="00e0b-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="00e0b-118">Cette technique permet aux développeurs de présenter leur application en magasin, ou autres médias, en superposant cette image par-dessus d’autres images.</span><span class="sxs-lookup"><span data-stu-id="00e0b-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![Exemple de capture de l’utilitaire de capture d’écran](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
