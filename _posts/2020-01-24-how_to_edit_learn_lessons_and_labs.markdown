---
layout: post
title:      "How to Edit Learn Lessons and Labs"
date:       2020-01-24 20:02:39 -0500
permalink:  how_to_edit_learn_lessons_and_labs
---

**Introduction:** Have you ever worked on a lesson or a lab, only to realize that it didn't look quite right - like maybe it had a couple of incorrect instructions, a sentence or two that could be phrased more clearly, or even a missing test? It happens. The people who write Learn's curriculum are (just like the rest of us) imperfect; as such, there are going to be a few problems with the lessons here and there. But how do you fix them? You could Raise an Issue, but that might take a while to get fixed, depending on how urgent the issue is and/or how easy it is to solve. Thankfully, there's another, arguably better option: opening a pull request on the lesson/lab itself! In this post, I'll show you how to do just that (*Hint: Just treat it like any other repository*).

## Open up the lesson's GitHub repository

Let's use the **Basic Nested Forms** lab as our example. Suppose we wanted to add a Summary at the top:

<img src="https://lh3.googleusercontent.com/dYjI_SlPZ7yBO4HTV8mLoo4QlXwpwwoIQBgCqZpPTyXYOMjvXKal4LsErnDVa-BMQM7yEpqMsnVkHiB4gs8lSnyxbM7YzZNac06tVi6NMPpicuOroSirnBMNRIgTih0T5Jg5ed5ctZcn16SdGC0MhfFjBzMvVQgB3y2tDsr9sIkkpTG0hBETpXxe8ZBpqzVYj0Osq218hNVMtBZJhNKwu36-lIYYIUoaFoEAZRWk5VMNrdu7p_jKLtokbxrnwYyApB03CNtWbPmbyMDpUJjvltVmvDbvSXn7cYJqh5-agvu2fl1PjVDIrF8qus4DRSUcigK67alnF9LEjAxncDmuLWlrFpdt8BsvTUQUbe7414BBDCTwC4T0KyPKrc1wcTUaEAP4-HqxKmSkY96-Dxhp9VyXxHfN4tyz5Dx-9kb3xu50_B9kNUW2xvRpDCiA9ROFtJg2B0A1-N8Pwlw8PZ5pnTSRTDRpc-vHMx82wVqhYiDsxVBOoewD-l4DImKvg-0wqvd0AS1tte8tiIKc_bMmMbNrXRO5p2Mo-MtQhgisZdksqk06vb0VVCvFPnK6mvwTnnm6g80Cwl5pjrOiimiK32JCeGahiPj83Q_ePl7jzRey5KmSG6uDgyYW1gfDO4GFBcccQq8KQXSdfYGD2SQVg94KHhv8n1Oh5kj7YYEAp38sg8MU-isL54E=w1110-h440-no" alt="Lab with Summary Suggestion at Top" />

The first thing we need to do is get to the lab's GitHub repository. You might be thinking, "OK. I'll just click on the **Open in Github** icon at the top of the lab." However, as I've been told, that usually takes you to the *wrong repository*. What you need to do is find the lesson at

```
https://github.com/learn-co-curriculum/[your-lesson-name]
```

I've found that the easiest way to do this is to click on the **Raise an Issue** icon at the top of the lesson:

<img src="https://lh3.googleusercontent.com/QOJNIfsjWrrDT62mBHzbxT5aA-qGyM0n0oR1AfiLkTeRdgycLv_nmf_Pfn0TYa50f8LJEtK7jIxzEO2PSCU3sX5FSXF1tUoOVuevphWhBHrDDE_2vv5tK7BZqmFrhm-kX682MiK7OUzlS2S5MRiGUzoatcIi5sg29eGBlF-o3CQwPWww2Nl490oxcBCGGyQvb9w_wsDhRl6bqQmZk3Wb8ORQedQzl7t_-aYAHH2YmNn57Sl5Km4xTgn_8bMAtMskjy1TcxXHdDc0JgCorFZEPxETUCfzxlJlKnUWuDGPQLiVK9jwy5zHb3htndkWAwHFJZMMUuRTylKfj2pdNM9X7-6ys5pRu0_a5RvoXgPzkni91k94qR4YbUfwPZovyjb2Pgm5HLvWpcZRcC1D4IXn_tC3JuitjeUDyQiSqknj6SeSmVricaEXXii_G6TL33k6HkRRq4Wms-8F_yfqPW7BSAF_1M3Tt3AAg4TPe1TNIUzDlBRrEJuIBeJO1CK2GAQ8hEWaRJQ3fMx51xQBYFpjgtvYDyF6Livz9Fv6Mo06p8tIyAj7dgKr724voepS_eu_IEx_YyvOCMriqUX_VPMhY7mWrMaY6mvBG_Ir1h-KJLqqfKPFoyLHm3PwPu_sjFxD1a5Tnrzzo-xlOJ3iMp3sodlioP15IshTOvBgc53plX8LKajf0BU6Mho=w600-h164-no" alt="Raise an Issue icon" />

This will take you to the correct repository:

<img src="https://lh3.googleusercontent.com/W0uO8Fnkk0wJpFVHQwHiKSieNwmy1xgfq6AYzizpznj-eiCFMOT5gew9L7U6TaMScXfngxmg9E6HI3iZ8phAWHnk71NmTQCNUWWTuhBmcq_Flp-LGiDXd-FvjpaRY2LYpMK0I_VxNzBl8J-_FTul5ENsMT-aZVcn_FDVDWK4p5YM-QYCmxRnDuonDJ6V_wh-Vuc1J8Lcn6DxSfm7l_IIaHL8ZmdJ5B1oCaIX5UQZHiJC_yyanFThVCRpJ9mPK1DE_ELt4A5IreMUTDi9oKtGG45esHh3zI_X5tTPuC6tIxdcCLadz9tuVx51X61nOzFw0TybU_GNdAEVkGSDnZiEuH-legWf-U4F1IHzyFs9N0jQ-_3L93lIxVh-ZLg9gdlVy5nnMlRicmacnAwChGG0sOiEOoSibNx9XHoCCGYap9JE0DzDyVn07rv_fn1fy29MpKyG7Sz8SZIKtR9xkxmHBovzoNYjGt80dwdBZK7Vf4HC3Dv7hbrwK5rIooj6ChdOYebE1_L7UiCTb2uSRvEix6jmpozuNwyjH7iToQjlp4JlK9TJhanuRW0-vEeCYDzdUkj2IIisPNYK3AovdnhFQCc0F2l9MAHMUKAniuQAoWyMNGkCYs-NyCsmcmtV5wdBjcceuKdJvEBRShh40QqG_nx5Iikor-QIZ69H0AQu2tMM4ITlmgulmQw=w880-h605-no" alt="Learn Lab Repository" />

> **Side Note:** This only applies to labs and codealongs, which have a blue **Open IDE** icon at the top. For regular lessons, which have a blue **Sandbox** icon, you can click on the **Open in Github** icon or the **Raise an Issue** icon; either one will take you to the correct repository.

## Fork the lesson

> **Side Note:** These next few steps are a review of forking, cloning, editing, committing your changes, and pushing to Github. If you want to skip all of that, go to the **"Review your changes on GitHub"** section.

Click the **Fork** button in the top right corner:

<img src="https://lh3.googleusercontent.com/5VUpOvB4xpxZ1dOth05lTM-Sx234QrcnBMw0pAFw6by5SVTZQa7BlfyqfVlxPx5bNkMmJKCTIBxS40LSV44IwN6KgtSyPNSdiNf6mA81tzTYP8dR6pHFwBCTtrYIx4rONmebq8H0lZM5L7IiZ6onUh7d1kaUAn3uyy1BaCAGCoTVWJU65aQzHOZaON4qwD3vCAD_bPfcdnwQnKawHSHurVKyq50Z6DKPbyizh5nFiAVJfvp738wyRnQ_a4ds12gDRNWaJ0hrP27-sakOapWCjOEobD2PHlAtjHV2XTB9_dwp8yimMxtTdE1UOHRNbfMEYee7YQXN4YNhudMfZjZPJtmajnWo2Pv393QlPqvqm70-nNJrc0lozJaBCOkFPpi1D-FB3D2jBI-l3lP3VxVu15BillQLqBvM3TdsHVAhlZANesV08WC18wxkn1vu0BMTK3-R6mBFg57kb6pR-_USI9KpnJcL_X1KoWsxujY9qGhDuKjY8k5OE_xbNJ283AH_Mr65sWISNw5YsMt7Y2ehGo59u8Ut7wwqWzQJi-SB9BDwIvHt-yexIQgwD4H8K0LbdFcAtYp2JXzP0TALtIEHbXfiAd43XDBu3A6sYvLsqHQPjx7pM4xVifxyDdIc5U6HCu9g8WiXhH8MgFI0BprYGOpx3QICj5WVOgZuyXWNdKYmwzmxlDvPfnU=w450-h160-no" alt="Fork Button"  />

You should then see a pop-up window:

<img src="https://lh3.googleusercontent.com/13Q_SLmHdrx735A69cq1vzM3lv2gCzrULBh3hKOceXJ7YORAcjnfx4ku3ezqPtGRX4pxRLCzMc6OinFnjvtkadqK6Mg6037XPacJd1LhpCto6ph2rOg_n2SfbAl5NcOVCnTl4HdmE3ZMm14nCZ_D4rL-jL0vnAzbTRdb2OrETAsY9gwoXhC-l1w3FAFHOak5LHW9oPGrzHW_KzTAnWU357K-V_Ff4x7vz-h6q0QLsLuDPUKpXJHyMTpQPrYwHf8AFiNtf88c03pWtdrl_PRjeCjcYAAZfDXVBqoH_QUF3C4YhDu2IJEF-5mT2G8F6LFJNko6fK6Kz125vxa33vxCf3ks8mUM92WtveQnxgcu3bV-00IXZJqny6f6Sr3Eks3yO0LnWCWv6-Wq7QJbN4F6wB2hMf-XXiWwh3swGPjWq7haVD8YStNvspQFIH87-0ffKaUA6njoTKF1r0iVFG-y_ffWgOGDCaL6iLHOH8TZ9DKAKOA9r4KWAuHOwOIpZxDvi0M-WSZlwaPLVB9ZPCRoKqlqKlcwR8oMJ8EWpFr0ozEvGULKHoOtqYok2cHFFLc0qFSuvwI6HjWDOIKa1SSosmRclqStrE3KjFs49XqMTmbguIVNw03zdWn1SHq4eurP_LMR_wyaIEVd_xnIbNGNCAO_OxG9ISr_pnTSP__Mo6wnHNmcXSSxvhQ=w540-h410-no" alt="Pop-Up Window for Fork Button" width="300" height="231" />

Just click on your profile icon and name, and wait a few seconds to be redirected to your newly forked repository. (If you've forked this repository before, the pop-up window will look a little different from the one above; just click on the link that it shows you, and you'll be redirected to your fork). You should see something like this: 

<img src="https://lh3.googleusercontent.com/mjD2kFWb9XB91w_1Py1vrzjrSZbpL2odteJHZEbEfGVVbUR-r2Hou4_Fw1wcaFCU9_ol9_Ht_4cLnUlzQPrrksUYwwZTIQ_YaE06_M1p5rgovV0PUnYqPgob-ou49kFj3o0fDLtbhYt04YQoMYBSNZ5pjEe19VQfx43oAviiUjdEt29-ev6awQxgZH8Tcli4QUgCKCmJmS-MvvL8JwGHd8SW83NTRxHA9TGhnBcJ6gC0-UJ0Kyd80zk0LFhjb6G5wd1uwtXaHWCexT4rDP-stCYoZUWTf9YgcK7P0wV6q0miK8xks5rESLLwgbEIHuxXoMk3_UWkmjF5Ni9_yygh1Zbs1d3In2503tkBfNOgXex14CnmBHjxSJ5dmzVrWJP0yFPCOPFuLRNSu0PMm9YlvWSbrYS5rEZxbVvM_14QsJh_OqNw59-XsDEpQ7jgt87rsJ_R9QhyBd04U7QyQCRo3Yv1LHrXjfSWHXhzCa-dUvZgKb-5p6Bm43qEzWr0i8Vct5kZ8haXkg5U6ZvGEBcYJUE7VkZdivNWbVOLjdIAZBpboshIvf-lb23XndtBevux1iC4eUqnu5U-W0DpLMmRiflrzrV2na8P4JGbcxNVkdi0D0K5R_qrFhb82OxS-0JoabmN9dO95AN03NCTLRBYVuRGtOHejnn4kXUXH9zA4-Ylja6ieLTgiw4=w1145-h745-no" alt="Fork of Lab Repository" width="750" height="488" />

## Clone the lesson into your IDE or local environment

Click the **Clone or download** button in the top-right corner, then click the clipboard icon in the pop-up window (I use SSH, but you can use HTTPS if you'd prefer):

<img src="https://lh3.googleusercontent.com/aHHaWrmJD5qrwEZs6cPACeZqH2pHVlrIHtL5wFYhnU2n-EZQ1aM3xBO2EbcwLDp0P3Ol4zegdm83qoCq7VGtiTWZ5FcK7N6xFHEBfw-M0-_C4wqC_W0xKM4jqLus5egrr1SRFMd-bDzE1HZBgmcSDBxlfw7SVETEhWFdVtXrjtOdZMN6X-1qCbDC2ma4Lp84AHxLFnBfR-rv5sw3_btslaONjf0Tp7p2Nr0ZYGhydd6tIlULLgDPwFvRML2XLoxRJOF26BQ1-yfB56WScDpzdfplYvdFRX7du0JDN8QZghFAbURKRjpTsrmqf3LSQ55mpoflQQk-tEzt5Rs-mT8aUFSqxe56fr0xyTb4R8iEvgtw6qGchWy0WqQ8drgjGXTXe8MhTz6h0ceu8AR7PUTsmpNXd_bhyNYlvrBGKBALMr8Wcd9JoFt8t6xAofFy3hLvouuZAsgE3LJJuuxA5Val_mTWHCRR0X0CKc7K8EAu3VQrX9NX9OuYw3U8_TkT_62oipGoC-O_GuTMNMkJdP6TC-OywAZ5LJJFwevzWdLpxFU7vCWf0YPi6pLIHEjyI9HQCt4OhcveFmRA-tHoU7U4GEv3iYhId-5y91mzX2xQ3tviSbPAZ3gZwZV9kTgC55-UiCPbjMsWydlm39rSmktp8co1ohzbHCjcI4kQ5m6DPUeo_qih6jHiy3s=w480-h320-no" alt="Clone or Download Button and Pop-Up" />

Now, go to your IDE or local environment, and write `git clone [paste-your-repo-name-here]`. The repo-name is what you copied from Github when you hit the clipboard icon. Now, `cd` into that new directory. I'm using VSCode in this case, but your command terminal should look something like this:

<img src="https://lh3.googleusercontent.com/Y8eyAGa6CLABwR_mwrP6nkrQntbytSA7hyH_bLMTKQFxwn-IQdXexTNXOg3pYXCwxRrct0sUrV-SdTLzBRgvdpnn9LnjvcisEO7wQdewWn1YDHUrOkqri-svxMWF-Fv7NHTYTELgWp5Dgo0wQc99tNYsmzrSWU8DY1QHv3-Yu9G0HgDQtSJDjOGmWJdv438JzJ4ZUXQVYMQ2hwhWnTkOIw5YPwS6GhO4k6OXBapVN4qsGw3MoS01TpsoM4g9AS3dgYovEKGgTU4v4_tFSUzMOKB5lokBGdG9P9_LiHV_orJXUkm-scVuIH1XEqEjs526ek9T5jVBPI0TUe8XNRhg6refxW70usW-JecixsavLVv1IuSUlKrM5jEfih21XC7bv-JFihHWkW-Ei0QaPFuIz0CRUr9UxrYCNCOQQZub84sihRclbZ6TdVW5jfK6sKTtp5b1sSepSiEremziWpkHY8pE2E4CYI5Sq6xQXrElQKF2M_I2ipdwvXv_jNKTN7pWIvV_tqpiCq7vmiFGf-ChxkaVltJZARBuwKFDH-iXE-Q0zfo_A9KmysdrWD6wddEQ8-6wjiSVJIVI_RCsAhYDAgYZcQ5jlhVaJ0PEyj_SEWuK07LZinKWRyd3U-yvabHV6eUFssAYsOq9yujl0dM_s11m-4Uymy3yeSsGE4bXHiB7oYW3jSfu0nk=w710-h300-no" alt="Command terminal with 'git clone' and 'cd' commands" width="568" height="240" />

## Make your changes to the lesson or lab

Let's add a Summary to this lab's README.md file:

<img src="https://lh3.googleusercontent.com/HUaPtKBUIxLxR-9_i4rRhrwRt0UltPi9SC0ZFElmDyE57i94BWXoESXqfh4NbXxddPsIVk10E6NF_INTnsrNhYE0tTAjM5W_VdAd83HjA7ftwSCf0mOsQf731m63HKt7YrQ8yGrqIV9vaFFSE22r1k1Pm-JGHpNqIbpq2gSue99oEFBRpG90sBwM8ah3g0anoXC89ud8zaQ2lmyCQU0qRR9ClXx-6ZTBUoL7POCi2FyK7IpXyORrUjIrrYV5UfnBdfUgO-10o19hWC6cyWHEBJcAomBPA5RU_PfuSKBwIfSC_8yfv7J3S35QRwghkkGCjddmKzQRRkl_uff9ZAbPc48a2hrGaLWi7geKXcvqM-0bFJXYkS25OrnIwBDnuZBTLuG9EnPbS6z5t2SM8IUWeOkMmDl8FjLdaBodN6h6Bcxy2U2oElhd6J2KOfrtdT30h2027ka-2TvOTFQ-UltgAcQBWvCyGFLPIlb7wNTfwUZzTFmiwS0k6yI97FKwc3HuokLSgnlMbde6dtaCtWdBN6eo0Dgz5C0j40yoQGffueN1GsQI9Pif13I5ZzYNxrUz4-IHoawHIeDlSVlIPOXtNyzDI2cP8pyv2BQt0N9B7K-82oMy6EE4dzvyuAyRVTxQldKEgw7uUq6ZP1YeA4P934CRQDcMd-9Z_Nu8V6dEFp0-cZ4vXNTXjAA=w1110-h630-no" alt="Summary added to lab Readme" />

> **Side note:** If you make any changes to a lab's test suite, be sure to try them out on your original lab first. Make sure the tests still work!

That all looks good, so we can move onto the next step.

## Add, commit, and push your changes

Let's stage our changes with `git add .` and commit them with `git commit -m "Your commit message here"`:

<img src="https://lh3.googleusercontent.com/SoDbO3BH3A_T6SvSdOUcec7hQgPRCskHI-jRvHwYeZvkPNiBzvyqKmQWjaNK-hHQ_XDk6DRtAUgs6WlDxN4dR7vxVRqQbI8ZNXbg48KOLXpUBAI1ohd7ATVbH97yY8RHBfGjR6x3IfxMQ0hcw_rtjgZnLqUq4nPUc5VZo8UiF_41AM4QRyCPBIH5bPt32URS6zkfxuh7_Y9P9u5JPvZ56tt6uVUjjQ6pDaCb6D0bYZmg62dnGAKTFiqdixJ63GMjniU3R4JjALSzbJwj03b-HShBvkVMzw2YgviXVoWQLokBNZUCOnZPUQsWzJCf_cgy1tZQnEpIplE8l5O65y7fBRILAAf45_oSSZjdeahtOcKw6geerb5poctUo42uYq4wm6kijJk0wUsveUJ46yCXyFGfPBd7SkKGSkMT90ZBmVPEhNw0xHlQ4jkOB-EK7sgFzxPKsPlZeE7zOPwEYm-iRUpHXYJ7NXSJb406ZWKSHhJJaFgnOdR24201DuSM-QFxvwpFu1j1O1lbGaSEN_pFlscJOd5a170VKkmMqS3TYuIrsvEnA_t2j_zAxdMouRzyue6SQ8cedT_aZPeymO4wz97qzgPcgKjiNBGHwFXobjuT7be92B4vaBH5kecu1N5FtEIBZziSfJ0eJdfBdtb1zmXoWf1QX0r0UxC6PdafWoGUpPVD6HUtVxY=w700-h230-no" alt="Adding and committing changes" />

If you want to add a description to your commit that explains your changes in more detail, just write `git commit`. That will open up a text editor. You'll be able to write and save something like this (I'm using "GNU nano", but you can use whatever text editor you want):

<img src="https://lh3.googleusercontent.com/2jew13-JvgwSdIYY85acSmE-rbk8-tAMxpv6_5nNV95nLFBsRs_n1ohyYEMI3tpJwg3ZIcFdoFfEf0ACBdSWHV0SkVYuoHZMfqTWjpj9W7AcM-XOrAkuFWXFqJjsP1MfVQiHucVgmGWtIy5glHEYZWU19kOw1QoEvUQg_c49nWKAn6rfhwqKPsSNH9fd8BUKWHkrMWOu7VEQ7un2MC_VqKq3ut9onbFFEa12m4pUqml_RTe9q73_nPWnBO938csg7qH76JxvB5eDVO4SccF-FnWWxJjwkUsJtDbOIik-2N9rjCEM1tdxsGdRADx4D23Ei6XDB9Rt6o_HV15ehV8CyjgVkAnGBVVfuRbgv9c3vuexJmyvGcADJgrPsM-kmSZW0c2C9qny8Z9mRgKms0XZRWP58abZOSx7hNw0gp4aGSdvL1VG3v3RSl0cuPDvpa7JWF-_73I4eETyffw0lsFgARBZcKkHntZOINi_a5MAvo1EhhJK8r-FGbOiOtp8HeNRLY5uEoI1WObs95ScC17lqnDCyPnpKU_Zk2naTErl4wlkhtv7sIrJWsQlhePL5KC4sXYi1Cyqj8jfwVeCzv6-LMrQ7q-eOLBMjV31U0COY9PdIthpxG1ksqQiokrMPTpA_FubiepURMm6Kpa9EgHyxMKi1_APMeUM8LBvGeqIL-d1qNMB9TpJlSc=w720-h300-no" alt="Git commit message and description" width="600" height="250" />

Finally, push your changes back to your repository with `git push`: 

<img src="https://lh3.googleusercontent.com/vXxa40em-Tbg0XunbSVqD7HEiqrNNlZJIb8UOOnN1ysfcY8KZH2USn1y1DxB-n8NAHRv1toM49Zvfe0v31HUUISGMcxQPNfbkK-avK8mqUqOkMz0MGjRSr5-nV1SDRuYcog51mTT1NBoI_U-M_KdxEI1U-_OWknEaIuLwAtWPkBW0N-eeDM--E4fO8dJXIX8eWk3z7PlR1urd8rOX9lJrUQpuKFsPx17wf0iO030JhO2Ddx4zsGr_i7yBwe97OSiRgRE37azLLprtGJmo_U3bMF-U5uzcGVLOND04WhSGWvzdKvK8TOOwX1yP4CcJT1BM9n_v9zWnBo16RQajcTL-OZC5Y5UwnZmlu6qJw_ORILWEQjDEdFSbaCERmWWfuqAAljg8rRHILPTpzKtQk0JhoRu28Il9WxnqMYocSkA5PtZI5DBZ4I4tHkNb2ChUopLPUUFkNAKv61Kl4SPEdPgKAc4fMbWJMxZKzjMQC22vphUFtk2hN_LwOectYVeB4n2CSo-Btm5cb1japg3Uv7EfhiuTjkFMOrsmxHy_nfncOzTUAqqijM6WJzC-XQgeIDxoZtOd2SS_3aXBYaW5XhIYaWtvf-46aUl-oJA60C9jI3ER03kCEboo2FxA8hwGgAp61qx-YfLDPpXWSETn5jaLGa3lHZyH3BLWMkpI60IB7pCK-RIVMK19Q4=w751-h301-no" alt="Using Git Push" width="600" height="256" />

## Review your changes on GitHub

Go back to your GitHub repository and refresh it. If you pushed your changes successfully, your repository will show your last commit, and it will be at least one commit ahead of the original lab's repository:

<img src="https://lh3.googleusercontent.com/W8b_pXqheF8fhTG1S_ApJwROqJqdSoLrfdueVCtRaI3YMuI50rr5gua18L1lPHbUHOJfn9jdUpgi44aq9WirSg0UOVMGrVpDMTGYpeesNDpV0QQeir2QOULq--WD5vcPgJUGX1BG6FXGmCA5cncOJqCzdI6uMaO55VQ0zSCqmIVsoapjCn27DcCjkxh_IvfCBfZmRgPI3ug9Dq2BzbA3s9af-d8r12HpGOpY9LXXaxJZwN-Ks9zf1QKQ8MZ5djXR-bklazUzWMNcosYHXlTDBJn8SGNGkrBcsM-jb7qCQnOoBjYatmmypROE6-l10FVZYHPv-UQeAKTqKM2nTgRLk3xrC48-wAmp_QLr0YRbVK4F3vWzTMJsl9psmrNt97Cdl9djGmyhc2kY3A16tA5EANfpC6Doz52Qc9cGKJRkhxiCFRr5rUvI_taIxV3j1jvJb6ToniSpsrfdDqhnduFuAhbCf00XxPA4qZE5B6X5XT62aE4utwBrNa5I_Ia788Rw75AMuUnJrL_Mtm-5ifVj2q0jBhGhqKug5qNI9-HuiKHB6FjyJ3Ir0AATDhE_g5BrF8oMzYvWHPBaA7t03AfKqj20FLxDrAWMHYiCXS7jUpE9938U1ZjPgSXXFA8Hzyr2GJ07eZS-k-sJ6YPZtEDtpWo07ewyScZe520K2iQJ5hRl7eqxVik-Sp8=w1131-h601-no" alt="GitHub repository with latest commit" width="706" height="375" />

Since we changed the README.md file, we can see our changes by scrolling down:

<img src="https://lh3.googleusercontent.com/3fer-w2ChvCL-iF0D-2Dd6JIGvxEmVMssLEbIfVsavvGQr_-zD-d7zQg5SMXOsFDWDVD12SOp-tK_QAEJqPmDgcEv24S8vg9tdESmVHbVY-ub80JtbvlBNkOxr1V87OtEn3Otf1ky1PLOYBkDBUjRfg8qCO5vvqSjGV7hA0ZB3l2zB6W7L8On_quSo5Rr6bfugevvqYeqVdNDHw7XLk51xlXlGSv305NBbPwJJIUj4BBHV3LTeafamUUqdP8vtSVwZzGcnNkfM08ClhgVQxhAW_w8YJUsH7vU3oJM9Egl7uV08MlfPZa6h3bVvpguFmJImZacXWDlvY8u1_0Cp_iY-ZmeqH4AfPkdK1ugxDn3JiyIUV7SJOQFq4jun_tUnKyf5X172u3bmit3iE3sV7EzMT5X7qn0YP8mSxxmUgoEIJBs7dea9y_uSmznCyeURv9akyHDuYruUCuiAxKT1_7xj7fSSauZJLEQKVAwqmHmpYHqQdAS2XtjN1so7HYJfYCnCAf0oAClCSp1EMwnEn7rffUobmeOxYdcqNqC_9uwrKGaPGb_mrkuU4WgimDZWu5vrOQq8T7rlz7BHd4rWqNhZz8XsdFox4uQqyRrU87TbicMQBvqSlq-_wYfNMUdT-JeZw23EBE0mrrNQNZzmbcEN7g-vc1ezjDpD3gKyQkrUORGILuiO-p8gs=w1091-h401-no" alt="Changes to Readme.md file" width="681" height="250" />

That looks good, so let's move onto the next step. If you want to change something else, then add, commit, and push your changes before coming back here.

## Open a Pull Request

We are finally ready to make a pull request! To do this, click on the **New pull request** button:

<img src="https://lh3.googleusercontent.com/GPPGoKaxcT9hALwHqJr6ZlngUTXWJWGT9e3KkYvkCc60CzlKPqw6ei5VVZdYj2y-fBVpnqhgY-pMNs30Y08xJ6xia3rpc2cOr0keJqLh0r-LmiMV4mtK7oLNmvi4TqDy-sxKwwZlH1heCTMsIP8I1_XdC3tuaiFobHjwE5gufGH6IKObl6oHKRPiweAIctLSDKdzTjzDi1DfgfLO5d4P5x5twQFSjgvqvU-P1ZPfeEgyk74u9G-EAxC-lV0L2GuYTW-Hjvmj9B0CpnzLKB9PGP8dLoscvFOJnD2ZAl_IRvpHHQ3vSTIaZtnOozZu07CD2X0VV1bjbDwrMEuRl-1Pq04cli--Jb8QJDKnXWlKMCeIPWfW0VDJQ_IBpbqWRTliR-QmyXInxciRje8d5N-SKAFN0JHuJw8SzcE-JQZqq_gm_J_jNYsDKMeqxQe1f8udjiJwKS0RZGosLrmSEVDZJN_ycdFluehdVzrElnVIe2KRwYs_foPzhoPWaWmHOxhzpk18yke3nGhcpUNhwL5J8d2_rN0HZFgugyN7K7ZZsx_0THHC2LV0Nxsd0sjHsXsIIsC-HaV0WL8PcWw6ZckxhaxEWcOH8fdi7X1nmwLAUKILDWiAZDRYFMn3JyTYZdHvK1CB7a3Y3SE9rCM-yJusRUXIBp_2gyEUaIV2yFdzZcdEvZs517Tbrr8=w1080-h326-no" alt="New pull request button" width="750" height="226" />

If your commits can be merged into the lab/lesson repository, you should see a screen with a green **Create pull request** button. It will look something like this:

<img src="https://lh3.googleusercontent.com/oCAEeGXJr-SKGck_11_71AOXCLY8K78NXJAz251hhiATrcdMlatnA9phaZaBquHsfYn78uZA0pHu8C7pC35heesTdNnCIoTo6vSf9WLrPrANnQHme7YvTLbsiTZza3j5rAv0ySKDtdL6EGESfhHHTIaHmwsGnFjTTsTD6mfAJBrDQ4b3NQVlImu0RwTKLCig2JpO5MjIspdwcX5IAXpoXkYM_ZJdCfAt3Vk8srmGdOSeiAGN6b2cIxj1vb7XOycxWiFgVcgK5VGi4wFujIyWmjkZa69U8hmrwAVuCYwiGLJHsQudGfB9S6PQ8uHcuT7t-Za_jwXB683Gl356MGRWI0qKCnXfaKCO9XMguSRYQf-Hvl-HQ8BK6mO09x-stMqoMOVpKJFdZVyiCkIMMQ384AhuYAihyG7JertKpVlMiLseEf4r2jA1Wb26_gMzzPg9ufSDyO1vO1_7oRK2ot65P5Lkhu-FWF4g7lNL4iAFimwcdcCY_cvoXnEqymbUd3KM4r9lQpv8El7FaPWpwBhLu6ZvtxMXv6K8KUH6yffT04PxyJSGsm95VAhAKQ-UI7e0Nd37Gjm3BmiuDyVsdJ9Y11NSkJLc7H_aomufhZXDYM2dgrVQJJbuzMFChw8Uxja6No7uDfp--mYtPy5ylxhCpZIvpvQLEYkYpi701zA52P81lDjeDlUqDcQ=w1245-h618-no" alt="Screen with 'Create Pull Request' button" />

When you click on that button, you'll be taken to the **Open a pull request** page. Here, you can review your commit and edit your commit message and description. Click the **Create pull request** button, and you're done!

<img src="https://lh3.googleusercontent.com/ayIsToWib_8_BfLcRg1S4GzWXCRIMHkeONuLUuaqbKfPKVtsyEQ-JoUFUaFScGJiVM3AlPWKEH8ZZu3Ec1i9tBosQvJKJe6GzUZMFMOIdb-BWT8t4ri3A74szasCHvqgf6U1Cl69DtUGSjTybAjDHzmsqjSlIReSygDDkv_0_-htWyVzPJ_zRRaJyBHljanCYJuYUkk5mt1G9_uYiC3Q4e9u7t2hHY7f2d2TDt-iCnVhCLBnTh9q1438Ql4yjykW0jjgALCa4U9G-ZyMBJ5ut_WcNvy-VXpxYUhaetkiZVXmhoZRiDPBX7Q1aZ8IQzk6D3NybG9hM6WgXb6exaM5wv6cglglziv1Uvk2vH2Ab5ryEfZe9ZG77p-5HS_KOO-3lo-eDbqUwuj8MNLR02GP6GK28h5S8ayXcLKO3gy5u2Q8NP2LKHp-ndC2Alz93X1J_ycHc3dXuunBD5XJpwSQheNzKZPkO5QYWxxGa3PMWxlL1wrAiW5RN1g-H0sac1uuBcHSe0OgwpdCKfeHR_S0GLVOKnElbuWbb-WHpdXDIn6HHRPwEeRjnbNH3CEUJhUk-Oh4O6FcdWEBj8jwV-4ZRBtjxutbikUP-wmkpWwxvRP9RQeNlFRO0sYLUmd15v13Bwi34BaUiFG7iqF_D3NaNe-0WKtBAg_udcYWL06tncVpMXui6nsMwuA=w956-h670-no" alt="Open a pull request" />

> **Side note:** Since this is just an example, I won't actually submit the pull request. The last thing I want to do is create a major headache for the Learn team!

If you're being *really* awesome by solving a raised issue with this pull request, go ahead and edit your commit description in the **Write** tab. Write something like "Fixes issue..." and paste in the URL of the raised issue. After you hit **Create pull request**, this will create a link to the raised issue on the pull request's page. (**Note:** I'm using a different example here, with an already-merged pull request for a closed issue.)

<img src="https://lh3.googleusercontent.com/gZG04iwoYo2fLPv6-NPEQ4q2k5-0onDW9mHXpOde523LOpQgrceGH7uhHaKQTg5D2DfRYrjZRqVhZ_ziCsg-M9N49AV_8FSvq5tTcLXsr5vDS26wPFS9MTqUgOUegFR0qULbD98zI7rGsyYs5yVvbUBHlZP4b7_tE-65Re1QNV0Ko-WbpZCGUj60FqYxMXMDeCJZvoQcA5_YBid2W7qXU0JRZmTra5qyf2cAOimG6rmqRdgSdBYVAkMcOg2HN6ZXxNJ2r8LLXC6ssGJ_b81YOrFhxLQ1JgYnqKBupIbHkxJEFsQy4VjMdOoy819UfNKD8WwboE-_BLLrvRo7dbV5EQFqO8zWm1MHTAED_94bzflMPxpxq6tD5CmHj-gopJBuXKKKnJKrOHtLU5FRBxOoTBWW4dY7dMm3Nq7R3wfY0sZ-e0U5nVbAP2IlX-A06ODcjYSW-pPl41bwV_oVJHl_ZsVR6N_vCB3O2JwSDgB_Teu5Udrjbqda8S7lIFzW_5Suf5e-MjGuMlf-HNS94X811JMBMLIacrJY13bjWqhFX5X45IQJ_s-82bMfxNHQiZl4TX0iSswy9LEjTS3a0M4Atv-a_FUoAaY518Jhle1zAliMvYVAOANWj9XIGijxH6rVlONM--5ryTXdP9TeYYjIxfg6DEKWEe1qrIti1405H2IpZb87a5ZndUs=w833-h444-no" alt="Merged pull request referencing closed issue" />

It will also create a link to the pull request on the raised issue's page:

<img src="https://lh3.googleusercontent.com/AyoVjD3Xq0MaCM057wEKo1mGeiCS7AJvqGiUNGhQ3US-IsZHOFqS6VQBM6-Tt07u_uWKTF6W1YzWM-imD2w3EFSUNzdK0DTTm6Vic5lNMkb5ucwaqF6YhYtkBjDE5QywYWhJRwnrKaFjirgXqVlZkekOiOiEVY4Zt467vrvCfCRG1rAQMlETNI4SyNkowjDBC9X-qgLCgu4qfmgYJ98aytBOCa83Oa-_GCEqAO95IoHEYCZA5BsUJSX_MahP-7sMLShugHHGEOwnuyIknuvWvhtxFMuDelpMZJCLOE8z65e3luSpNnuonX8AdySGd0eoRf1v1HjhKSIy1Rdq45HLaSUU6DJaoWLWQneZrBo7o8UwvHMwYCfea7pdKuTQuivJep8Czhfc6_2-Pqz0l1bg5tIb0uwKUstVmiWsHTLpurJiRfF4BQgRGMIeiIgK7KCHud3kYlD2GA6EUdlqrXCnYYuQYXJg0cgOxEYViMTdLXxPoLaknxnmRiuknHmTLdI06n93k2VhfmNwqh-7Pu5xm_k90CYAE5pTygliN7ZlFZ2gVMSej8liGwWzFIKdg5cu6xV1US83epGhpKinPEQc1QBAGY24erljtuoqsiLqEGXBXzPqUoFcVI7BpPfDXMYmbpUSnfLsypqtw2MItWeB-vhNwlp0PJ08mSJmOngbNBgz5qdRDaAteaE=w833-h384-no" alt="Closed issue referenced by merged pull request" />

Cool! There's just *one* more thing that we may need to do.

## Make additional commits as needed

Suppose that you made a mistake with your pull request, or you've realized that you forgot to make an important change. What do you do, open another pull request? Thankfully, the answer is no. Just make a new commit, and push it to GitHub. That commit will be added to your pull request *automatically*.

**That's it!** Now you can make changes to any lesson/lab that you want! (But please make *good* changes; be nice to the Learn team.)

## Hold up! Why would you want to do all of this in the first place? Why not just Raise an Issue?

To be fair, if you don't know how to solve the problem, it's probably better to Raise an Issue. However, if you *can* solve the issue with a pull request, then I *highly encourage it*. Here are a few reasons why:

1. It benefits the *Learn team* a great deal! It's much easier (and quicker) for them to merge in an existing pull request, than to read over an issue, familiarize themselves with it, figure out how to solve it, make the needed changes, and merge them in.
2. It benefits *other students*. The quicker that the lesson/lab is fixed, the less likely other students will have the same problem that you had. And for those students who *have* had the same problem, they'll be able to look back at the lesson and see that it's been fixed! This is especially true if your pull request fixes an issue that they raised.
3. It benefits *you*. For one thing, you'll get experience with fixing a real-world problem, and you'll get to practice using Git and GitHub, both of which are skills that a lot of web development jobs (among others) are looking for. And - let's face it - you'll feel good doing it! "Virtue is its own reward", after all, and you'll get to say that you contributed to the Learn curriculum.

So, you'll wind up helping out a lot of people just by submitting a pull request. Why not give it a shot?

## More Information

* [Pull request basics](https://github.com/learn-co-curriculum/github-pull-request-basics)
* [How to make a commit with a message and description](https://stackoverflow.com/questions/16122234/how-to-commit-a-change-with-both-message-and-description-from-the-command-li)

## Feedback

I am always open to comments and suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.
