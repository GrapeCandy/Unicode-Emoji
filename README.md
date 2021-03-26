# Unicode-Emoji
Explain the concept of Unicode & emoji.

1.About Unicode
----------------- 
##### 1-1. Concept of Unicode
<pre>
<code>
  1. Unicode is an industry standard designed to consistently represent and handle all characters in the world on computers.   
     
  2. This standard includes ISO 10646 character sets, character encoding, character information databases, algorithms for handling characters, etc.     
     
  3. The purpose of Unicode is to replace all existing character encoding methods with Unicode.     
     
  4. Unicode has two mapping schemes: Unicode Transformation Format (UTF) encoding, and Universal Coded Character Set (UCS) encoding.  
</code>
</pre>
   
##### 1-2. Unicode Plane
> * Logically divided the whole Unicode.       
>    
> * Number 0 (Basic multilingual plane) to number 16 is 17 in total.

##### 1-3. CodePoint
> * The code value assigned to the Unicode character.   
> * There are two sub-scopes within the full range of the code point.   
> * The default multilingual plane (BMP) is in the **U+0000 to U+FFFF** range. This 16-bit range provides 65,536 code points that are sufficient to cover most of the world's write systems.   
> * Code points are in the range **U+10000 to U+10FFFF**. This 21-bit range provides more than one million additional code points for other purposes, such as less-known languages and emojis.   
> * **[Codepoint Creation Formula]**   
>   code point = 0x10000 + ((high surrogate code point - 0xD800) * 0x0400) + (low surrogate code point - 0xDC00)   
>      
> * **[Relationship between BMP & Supplementary code points]**
<img src="https://docs.microsoft.com/ko-kr/dotnet/standard/base-types/media/character-encoding-introduction/bmp-and-supplementary.svg" width="60%" height="60%" title="Unicode BMP" alt="Chart"></img><br/>

##### 1-4. Basic multilingual plane (BMP)
> * The first (zero) plane of the Unicode, **from U+0000 to U+FFFF**.      
>    
> * The BMP contains almost all modern and special characters, most of which consist of Han-gul, China, and Japan integrated Chinese characters.   
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Roadmap_to_Unicode_BMP_de.svg/800px-Roadmap_to_Unicode_BMP_de.svg.png" width="60%" height="60%" title="Unicode BMP" alt="Chart"></img><br/>

##### 1-5. Supplementary Multilingual Plane (SMP)
> * It is used in old letters, music symbols, and mathematical symbols.   
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Roadmap_to_the_Unicode_SMP.svg/1100px-Roadmap_to_the_Unicode_SMP.svg.png" width="60%" height="60%" title="Unicode SMP" alt="Chart"></img><br/>

##### 1-6. Supplementary Ideographic Plane (SIP)
> * It mainly contains Chinese characters that are not included in the initial Unicode system.
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Roadmap_to_Unicode_SIP_multilingual.svg/800px-Roadmap_to_Unicode_SIP_multilingual.svg.png" width="60%" height="60%" title="Unicode SMP" alt="Chart"></img><br/>

##### 1-7. Surrogates
> * Surrogate pairs are Unicode areas designated for use only for UTF-16 encoding, with **U+D800 to U+DBFF** (**high surrogates**) and **U+DC00 to U+DFFF** (**low surrogates**).   
> * Characters outside the BMP region are represented by a combination of high and low surrogates in UTF-16.   
> * It is technically possible to express in UTF-8 but explicitly prohibited by standards.   
> * In Linux, wchar_t is 32-bit, but Windows supports 16-bit, so wchar_t cannot fully contain a single Unicode code.   

* * *
2.About Emoji
--------------
<pre> <code>
“🖤”.length() => 2
“❤️”.length() => 2
“👦”.length() => 2
“👦🏾”.length() => 4
“🚵‍♀️”.length() => 5
“👨‍👩‍👦‍👦”.length() => 11   
</br>
The length varies depending on the type of Emoji.
</pre> </code>
    
##### 2-1. Concept of Emoji
> * a small digital image or icon used to express an idea, emotion, etc.

##### 2-2. Categorization of Emoji
> 1. Simple 2bytes character
> > * Emoji with unique **2bytes** Unicode code point   
> > > 🖤 (U+1F5A4)

> 2. Combination of Variation Selector-16 (VS16)
> > * VS16 is a non-visible character designated as a code point **U+FE0F**.   
> > * Convert special symbols from Emoji's days to emoji.   
> > ♀️ (♀ U+2640, U+FE0F)   
> > 🏳️ (🏳 U+1F3F3, U+FE0F)

> 3. Emoji Modifier Fitzpatrick
> > * Unicode 8.0 has added a code point that expresses the color of human skin.   
> > * This is the Emoji Modifier Fitzpatrick Type, which allows us to express five more things in combination with the first yellow skin.   
> >    
> > **[Emoji Modifier Fitzpatrick Type]**   
> >  🏻 Light Skin Tone   
> >  🏼 Medium-Light Skin Tone   
> >  🏽 Medium Skin Tone   
> >  🏾 Medium-Dark Skin Tone   
> >  🏿 Dark Skin Tone   
> > 👦🏾 (👦 U+1F466, 🏾 U+1F3FE)

> 4. Zero Width Joiner Combination (ZWJ)   
> > * Use to combine letters with letters to replace them with combined characters.   
> > * This is an invisible character designated as CodePoint **U+200D**.   
> > 👨‍👩‍👦‍👦 (👨 U+1F468, ‍ U+200D, 👩 U+1F469, ‍ U+200D, 👦 U+1F466, ‍ U+200D, 👦 U+1F466)   

> 5. Flag (For Mobile)   
> > * Flag Emoji that supports **mobile** environments only.   
> > 🇦🇺 (🇦 U+1F1E6, 🇺 U+1F1FA)
 
> 6. Complexly coupled Emoji   
> > * Both symbols, ZWJ, and VS16 are expressed in combination.   
> > "🚵‍♀️ Woman Mountain Biking" (🚵 (U+D83D U+DEB5), ZWJ (U+200D), ♀ (U+2640), VS16 (U+FE0F))   
