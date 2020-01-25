---
layout: post
title:      "How to Edit Learn Lessons and Labs"
date:       2020-01-24 20:02:39 -0500
permalink:  how_to_edit_learn_lessons_and_labs
---

**Introduction:** Have you ever worked on a lesson or a lab, only to realize that it didn't look quite right - like maybe it had a couple of incorrect instructions, a sentence or two that could be phrased more clearly, or even a missing test? It happens. The people who write Learn's curriculum are (just like the rest of us) imperfect; as such, there are going to be a few problems with the lessons here and there. But how do you fix them? You could Raise an Issue, but that might take a while to get fixed, depending on how urgent the issue is and/or how easy it is to solve. Thankfully, there's another, arguably better option: opening a pull request on the lesson/lab itself! In this post, I'll show you how to do just that (*Hint: Just treat it like any other repository*).

## Open up the lesson's GitHub repository

Let's use the **Basic Nested Forms** lab as our example. Suppose we wanted to add a Summary at the top:

<img src="https://lh3.googleusercontent.com/LDIdcLTaSe173IQA3AoCI9cFFiR9v0ZbDzDapEvZXQK-u-GW0mA_4vt4pTHhIlCKQzEGJ2w0P4UG9TZDGa1hV0q-eUO-LHs6V9s_9IArlH4KeELokKMlf4cihSeRCZcflF6t6tJ2xwRTt5cpEk2sMDvlsyKWbTjUeZmxJpZZwQJFvD2fWyys0iwWEziFkChXNVUDWxyopIzBg-TpeumOLHc4H5Gg9bzHVLLhiOvfTmBz7joKqg-nAQc-cxmMCPE4B3VgAXRqXRzz57uQ96jnqF5avH8OUPhGD7BoJfWQsnaHdkUsK1iBjdofHWQRE3AHMpQZwbFBa4GsY-jh3SqnY04SaHDFDsTUcPb5CUxC3C2kQYr9Wg6my5OKgZ2lxhxsBX9SULzhOKxU2IQ0xuw41EJlZgn9Ci6IzBZk0VwBAK_6tfjvOl_MJbXq05tGbyI5aqza5i6RGlEUiQIs00MSmw2VScqKs12qrl5GMOCCtBqXysrPKBR293k-yb9FtybU4zXjUNBq_D2Hlz5e8NBzCh1MFf-1Hu8_yC_bEx70qSgFn3beJPj_BZc5RyJEUrULazm1fShTOJJCu2GgeGeneJJvlYfg_t57tAfFCWCvrZ8qNrCSeQyy0JjHVrIlBdH5gbVZMMr944T8pPdGhzUu61IT6PkLWDi6gRS_DYzqFEUVuGbUeNHdBqA=w1341-h703-no" alt="Lab with Summary Suggestion at Top" width="600" height="300" />

The first thing we need to do is get to the lab's GitHub repository. You might be thinking, "OK. I'll just click on the **Open in Github** icon at the top of the lab." However, as I've been told, that usually takes you to the *wrong repository*. What you need to do is find the lesson at

```
https://github.com/learn-co-curriculum/[your-lesson-name]
```

I've found that the easiest way to do this is to click on the **Raise an Issue** icon at the top of the lesson:

<img src="https://lh3.googleusercontent.com/L-Rl0wtlPG15bfkN3ZTv-_GCxmh6Eg_sEO6yBZ2-N9fgtN_W5UIQKetTuZVJDZw_zgGTQm6BkRfFKYA2-Kll-pKl27uSiSxIO0MltyvU8X01bABEgFx4aO97W2gTX8GmTO54BDJviJbR_CCqcInElHHkw90iQ2cch1uc1sQyppHokhhYvCuKGtt6e0NkHUi2du0lsFDS14p76tKwWfJdxKPWKLImKfq6gfW6quqaE66ka4nJYNnXd-mTFsEUi0uKUdPSD2jnnsVKZAgf3L_02Z1ejP6CiUvFfTk7L85I2PXz56G8xp7Vq-OnLeiKHOi1K_1iznTtF5n3o0hBiYVt8Lfgja7KrAf_krtNa9EB5dkpsJCM4-uFETqOu_jyFddy-SJZFNhqBumsckZ52r67JxKq7VMP-fNvXMTHpCBp_InYd3a2lNMtkqgrgS5Xi8LgolRI1eOYEEX8ybIm9DFbTvBc_LGfd7BCPPcOEZaglVi5w0GpvQ7o5jQg7IeT0YZ_-y0_DUCHIfANNI-eVRDiI0Ir1wIG0ICVR02WUrcBYai8ZhGeQd_xOxLU6WzHagorbUhPAhRDqWlz3tovg0wTZ4HmmyM7zmUtNJEHtw7s3NT2e6GextlmKDNG1q9lc3TtKvdsY-iiiZiBwotYpksTxwoLGOKAKSo0z_EY9csrP8PH6nJKsv9hUdk=w1341-h164-no" alt="Raise an Issue icon" width="800" height="98" />

This will take you to the correct repository:

<img src="https://lh3.googleusercontent.com/LI2BtEl_tpYD8ibNfykR_cP__UIzYMO824yP9Cm1rxSQzWZFABszqI9P0IekwO0m-lRQmD7AhDLPOkk7fee2mtHjByOQKNHLdY10dTES82gLQ3eFG1eIDzZBbqYCzr_mUdXcoJuvvJFgx78zg55hCZObeUbYpPRKv5C8tQj2eTVCVYOyKTv1YMrtBS17gK1MLySx2MbyOWPPax3yZr6mzp07y5qw2_WrYIc1aLUDzs5f3agaFwSvV50WgUNm5LrOjMl_Yp9BtnD3zyJc_fCx4Kvt-7iDrGpG0h2KtC8s5IYy7aKJ4k7TDeJzWr1GCVkodxV1OT9dDu6AK-0mGtfOpjFtmb7DEJGrci3xkOvjOIsFYyRuLZrKuQUebk_rMzg48FAJm3MUWBA4OvAcu45tsbhD3iyiaFDLPPncWuCICYqVBapcqoVnMIIrR4fPNGw_Dhp1SZPX97vugX1J-pm_J93ZLnawQC7097lLGE5vxB9KlsC2qXcOto15HTvcG2oZ-Sxw6QGpLQE8so8xZmJd5UnPK59LiQrH9fOYs09qmGfXr1sVuSUbMli5XlVeAQlfu_2DQ9pUIMfTtKJX3eNN0L18nmhgs_wC50TD4lM17264PajRdd58Wil6tAxnVyj9eKmk9qbbl_cr_KjiZXGbE2s2VdzI7sYreOlimZLrKQ0zz_IaKbGsJk8=w1161-h750-no" alt="Learn Lab Repository" width="500" height="323" />

> **Side Note:** This only applies to labs and codealongs, which have a blue **Open IDE** icon at the top. For regular lessons, which have a blue **Sandbox** icon, you can click on the **Open in Github** icon or the **Raise an Issue** icon; either one will take you to the correct repository.

## Fork the lesson

> **Side Note:** These next few steps are a review of forking, cloning, editing, committing your changes, and pushing to Github. If you want to skip all of that, go to the **"Review your changes on GitHub"** section.

Click the **Fork** button in the top right corner:

<img src="https://lh3.googleusercontent.com/kL_QOtpG-4uOa4bNuc8AsTCyD7PF-e19wn9cuxMbzzOSWNcOD4IEKeEj9ReagNijw2kpTaQmlSJNbYpv7cQFqOkvdmEyW8ARhqpKxyPjT_PofKWbATzLivbxpm4DgA1gRD5eqO74QZLrpEk5PmgE4qmwlEnxOmB3clNh59psGhFSUb3QQhjc1eQ36uhNCy-jZDYVLDvZb2ekUU-qlMtNTlc3fsp3DcUKhjcCaEReta28kNFk46gqdvx5P7SJWN3tLfDCcLg7J5gzhrM5KoQcfveTD3S7ViY_tsrEMQCKweBeXvBF1xCd3__fwI1X3CKQbr1EFgUdSruUn3P5-AoxEbESqVoJ25V1AU-RyKSdcrRAzmexWNXfAG8xk4raMul2-_HQyGEteolXc74zgqb-mjB4AwPTVwe10jSDc1Dl6z_-e2PQoQiZbwW33-CYgw9QmQqzX_1ip9C6Q3w6-OuLhbAGCSvHytbaQ6VDXqDfipqv_kkUDi1psyHPOUW8VqWQsERtUhhIF6K5R30gPCjRspcI3qeuZf5Ie4ZW6pZ0u_LqYj_YPe3XSz3TaZZN3bsdlt2SAOSHj_SHXNsA_DUBhtppQDdeWI4ALy9xyhr_FQb-vP4IMqiP56KBQ_zwJnIfkbzZoSCeXr7F2J8utLjxegjapW4h6Gsti5ZKyQxTdCz431QA3hL8rYw=w1121-h160-no" alt="Fork Button" width="800" height="114" />

You should then see a pop-up window:

<img src="https://lh3.googleusercontent.com/13Q_SLmHdrx735A69cq1vzM3lv2gCzrULBh3hKOceXJ7YORAcjnfx4ku3ezqPtGRX4pxRLCzMc6OinFnjvtkadqK6Mg6037XPacJd1LhpCto6ph2rOg_n2SfbAl5NcOVCnTl4HdmE3ZMm14nCZ_D4rL-jL0vnAzbTRdb2OrETAsY9gwoXhC-l1w3FAFHOak5LHW9oPGrzHW_KzTAnWU357K-V_Ff4x7vz-h6q0QLsLuDPUKpXJHyMTpQPrYwHf8AFiNtf88c03pWtdrl_PRjeCjcYAAZfDXVBqoH_QUF3C4YhDu2IJEF-5mT2G8F6LFJNko6fK6Kz125vxa33vxCf3ks8mUM92WtveQnxgcu3bV-00IXZJqny6f6Sr3Eks3yO0LnWCWv6-Wq7QJbN4F6wB2hMf-XXiWwh3swGPjWq7haVD8YStNvspQFIH87-0ffKaUA6njoTKF1r0iVFG-y_ffWgOGDCaL6iLHOH8TZ9DKAKOA9r4KWAuHOwOIpZxDvi0M-WSZlwaPLVB9ZPCRoKqlqKlcwR8oMJ8EWpFr0ozEvGULKHoOtqYok2cHFFLc0qFSuvwI6HjWDOIKa1SSosmRclqStrE3KjFs49XqMTmbguIVNw03zdWn1SHq4eurP_LMR_wyaIEVd_xnIbNGNCAO_OxG9ISr_pnTSP__Mo6wnHNmcXSSxvhQ=w540-h410-no" alt="Pop-Up Window for Fork Button" width="250" height="205" />

Just click on your profile icon and name, and wait a few seconds to be redirected to your newly forked repository. (If you've forked this repository before, the pop-up window will look a little different from the one above; just click on the link that it shows you, and you'll be redirected to your fork). You should see something like this: 

<img src="https://lh3.googleusercontent.com/mjD2kFWb9XB91w_1Py1vrzjrSZbpL2odteJHZEbEfGVVbUR-r2Hou4_Fw1wcaFCU9_ol9_Ht_4cLnUlzQPrrksUYwwZTIQ_YaE06_M1p5rgovV0PUnYqPgob-ou49kFj3o0fDLtbhYt04YQoMYBSNZ5pjEe19VQfx43oAviiUjdEt29-ev6awQxgZH8Tcli4QUgCKCmJmS-MvvL8JwGHd8SW83NTRxHA9TGhnBcJ6gC0-UJ0Kyd80zk0LFhjb6G5wd1uwtXaHWCexT4rDP-stCYoZUWTf9YgcK7P0wV6q0miK8xks5rESLLwgbEIHuxXoMk3_UWkmjF5Ni9_yygh1Zbs1d3In2503tkBfNOgXex14CnmBHjxSJ5dmzVrWJP0yFPCOPFuLRNSu0PMm9YlvWSbrYS5rEZxbVvM_14QsJh_OqNw59-XsDEpQ7jgt87rsJ_R9QhyBd04U7QyQCRo3Yv1LHrXjfSWHXhzCa-dUvZgKb-5p6Bm43qEzWr0i8Vct5kZ8haXkg5U6ZvGEBcYJUE7VkZdivNWbVOLjdIAZBpboshIvf-lb23XndtBevux1iC4eUqnu5U-W0DpLMmRiflrzrV2na8P4JGbcxNVkdi0D0K5R_qrFhb82OxS-0JoabmN9dO95AN03NCTLRBYVuRGtOHejnn4kXUXH9zA4-Ylja6ieLTgiw4=w1145-h745-no" alt="Fork of Lab Repository" width="500" height="325" />

## Clone the lesson into your IDE or local environment

Click the **Clone or download** button in the top-right corner, then click the clipboard icon in the pop-up window (I use SSH, but you can use HTTPS if you'd prefer):

<img src="https://lh3.googleusercontent.com/aHHaWrmJD5qrwEZs6cPACeZqH2pHVlrIHtL5wFYhnU2n-EZQ1aM3xBO2EbcwLDp0P3Ol4zegdm83qoCq7VGtiTWZ5FcK7N6xFHEBfw-M0-_C4wqC_W0xKM4jqLus5egrr1SRFMd-bDzE1HZBgmcSDBxlfw7SVETEhWFdVtXrjtOdZMN6X-1qCbDC2ma4Lp84AHxLFnBfR-rv5sw3_btslaONjf0Tp7p2Nr0ZYGhydd6tIlULLgDPwFvRML2XLoxRJOF26BQ1-yfB56WScDpzdfplYvdFRX7du0JDN8QZghFAbURKRjpTsrmqf3LSQ55mpoflQQk-tEzt5Rs-mT8aUFSqxe56fr0xyTb4R8iEvgtw6qGchWy0WqQ8drgjGXTXe8MhTz6h0ceu8AR7PUTsmpNXd_bhyNYlvrBGKBALMr8Wcd9JoFt8t6xAofFy3hLvouuZAsgE3LJJuuxA5Val_mTWHCRR0X0CKc7K8EAu3VQrX9NX9OuYw3U8_TkT_62oipGoC-O_GuTMNMkJdP6TC-OywAZ5LJJFwevzWdLpxFU7vCWf0YPi6pLIHEjyI9HQCt4OhcveFmRA-tHoU7U4GEv3iYhId-5y91mzX2xQ3tviSbPAZ3gZwZV9kTgC55-UiCPbjMsWydlm39rSmktp8co1ohzbHCjcI4kQ5m6DPUeo_qih6jHiy3s=w480-h320-no" alt="Clone or Download Button and Pop-Up" />

Now, go to your IDE or local environment, and write `git clone [paste-your-repo-name-here]`. The repo-name is what you copied from Github when you hit the clipboard icon. Now, `cd` into that new directory. I'm using VSCode in this case, but your command terminal should look something like this:

<img src="https://lh3.googleusercontent.com/Y8eyAGa6CLABwR_mwrP6nkrQntbytSA7hyH_bLMTKQFxwn-IQdXexTNXOg3pYXCwxRrct0sUrV-SdTLzBRgvdpnn9LnjvcisEO7wQdewWn1YDHUrOkqri-svxMWF-Fv7NHTYTELgWp5Dgo0wQc99tNYsmzrSWU8DY1QHv3-Yu9G0HgDQtSJDjOGmWJdv438JzJ4ZUXQVYMQ2hwhWnTkOIw5YPwS6GhO4k6OXBapVN4qsGw3MoS01TpsoM4g9AS3dgYovEKGgTU4v4_tFSUzMOKB5lokBGdG9P9_LiHV_orJXUkm-scVuIH1XEqEjs526ek9T5jVBPI0TUe8XNRhg6refxW70usW-JecixsavLVv1IuSUlKrM5jEfih21XC7bv-JFihHWkW-Ei0QaPFuIz0CRUr9UxrYCNCOQQZub84sihRclbZ6TdVW5jfK6sKTtp5b1sSepSiEremziWpkHY8pE2E4CYI5Sq6xQXrElQKF2M_I2ipdwvXv_jNKTN7pWIvV_tqpiCq7vmiFGf-ChxkaVltJZARBuwKFDH-iXE-Q0zfo_A9KmysdrWD6wddEQ8-6wjiSVJIVI_RCsAhYDAgYZcQ5jlhVaJ0PEyj_SEWuK07LZinKWRyd3U-yvabHV6eUFssAYsOq9yujl0dM_s11m-4Uymy3yeSsGE4bXHiB7oYW3jSfu0nk=w710-h300-no" alt="Command terminal with 'git clone' and 'cd' commands" width="568" height="240" />

## Make your changes to the lesson or lab

Let's add a Summary to this lab's README.md file:

<img src="https://lh3.googleusercontent.com/v5TU12kTcYnGWcVJgEdDGfqysvX-UniHB2RtoYYP9-Y7Ev05kR9GuryVpWmlqfslpHljLRV5LNLHX9TDsiPK7mLvrrpZNbnGYP83_pLmdqYKT0DKHCnCkM92EzPZuMNrKIRk3tOnn1O32ijY4DjoxKPOWwGUe1rlZC6d6brFxAy2ptvIyn_lFRNcuIYxVGnXQL2i94fpTAyeItGhTWPWtH0OUg0yDvtbjlxm0XnKKCLFYr-a7JHdP-K7GY-_5HSZi_jafsSLyFH2tWAtyrcbRR_zWGYWLISmAaG2nu4lspog01g1EQMMoGaOie4ajCN-F9z5QYXiHhESdEUYAIfgR7eShUtK1AuBi4My8xQK9XSullNMUF0o0yo6tOU2m8IiNjl3ItFUaoKc2Gq8vx8RR9GRtRO4_AUil9uabpybdJkZg-4S_H2OHXfM9KKSS94TuGEk2-zU70aqF-1pBfnx5fc7oBlDxbg2ejJQ8GImNFDfNoebApODykO9JwNKezfdzSew--lT7-GgXJbpy7DWfqG81dvqfRik_H4BXQ7-_i9aLtRrTrEVdrxKSUDwFGz87dqiW1HN8jq_2eqx0N0FBPHV-11KAALzoQiZg8YpSPSKE3f0NVLTty-cfi5TIR8lmwOBU7UkLfZA_IP_ssRRsv91jufBY-nJZhu9vPI913So28km4OzOzQc=w1333-h630-no" alt="Summary added to lab Readme" width="666" height="315" />

> **Side note:** If you make any changes to a lab's test suite, be sure to try them out on your original lab first. Make sure the tests still work!

That all looks good, so we can move onto the next step.

## Add, commit, and push your changes

Let's stage our changes with `git add .` and commit them with `git commit -m "Your commit message here"`:

<img src="https://lh3.googleusercontent.com/SoDbO3BH3A_T6SvSdOUcec7hQgPRCskHI-jRvHwYeZvkPNiBzvyqKmQWjaNK-hHQ_XDk6DRtAUgs6WlDxN4dR7vxVRqQbI8ZNXbg48KOLXpUBAI1ohd7ATVbH97yY8RHBfGjR6x3IfxMQ0hcw_rtjgZnLqUq4nPUc5VZo8UiF_41AM4QRyCPBIH5bPt32URS6zkfxuh7_Y9P9u5JPvZ56tt6uVUjjQ6pDaCb6D0bYZmg62dnGAKTFiqdixJ63GMjniU3R4JjALSzbJwj03b-HShBvkVMzw2YgviXVoWQLokBNZUCOnZPUQsWzJCf_cgy1tZQnEpIplE8l5O65y7fBRILAAf45_oSSZjdeahtOcKw6geerb5poctUo42uYq4wm6kijJk0wUsveUJ46yCXyFGfPBd7SkKGSkMT90ZBmVPEhNw0xHlQ4jkOB-EK7sgFzxPKsPlZeE7zOPwEYm-iRUpHXYJ7NXSJb406ZWKSHhJJaFgnOdR24201DuSM-QFxvwpFu1j1O1lbGaSEN_pFlscJOd5a170VKkmMqS3TYuIrsvEnA_t2j_zAxdMouRzyue6SQ8cedT_aZPeymO4wz97qzgPcgKjiNBGHwFXobjuT7be92B4vaBH5kecu1N5FtEIBZziSfJ0eJdfBdtb1zmXoWf1QX0r0UxC6PdafWoGUpPVD6HUtVxY=w700-h230-no" alt="Adding and committing changes" />

If you want to add a description to your commit that explains your changes in more detail, just write `git commit`. That will open up a text editor. You'll be able to write and save something like this (I'm using "GNU nano", but you can use whatever text editor you want):

<img src="https://lh3.googleusercontent.com/2jew13-JvgwSdIYY85acSmE-rbk8-tAMxpv6_5nNV95nLFBsRs_n1ohyYEMI3tpJwg3ZIcFdoFfEf0ACBdSWHV0SkVYuoHZMfqTWjpj9W7AcM-XOrAkuFWXFqJjsP1MfVQiHucVgmGWtIy5glHEYZWU19kOw1QoEvUQg_c49nWKAn6rfhwqKPsSNH9fd8BUKWHkrMWOu7VEQ7un2MC_VqKq3ut9onbFFEa12m4pUqml_RTe9q73_nPWnBO938csg7qH76JxvB5eDVO4SccF-FnWWxJjwkUsJtDbOIik-2N9rjCEM1tdxsGdRADx4D23Ei6XDB9Rt6o_HV15ehV8CyjgVkAnGBVVfuRbgv9c3vuexJmyvGcADJgrPsM-kmSZW0c2C9qny8Z9mRgKms0XZRWP58abZOSx7hNw0gp4aGSdvL1VG3v3RSl0cuPDvpa7JWF-_73I4eETyffw0lsFgARBZcKkHntZOINi_a5MAvo1EhhJK8r-FGbOiOtp8HeNRLY5uEoI1WObs95ScC17lqnDCyPnpKU_Zk2naTErl4wlkhtv7sIrJWsQlhePL5KC4sXYi1Cyqj8jfwVeCzv6-LMrQ7q-eOLBMjV31U0COY9PdIthpxG1ksqQiokrMPTpA_FubiepURMm6Kpa9EgHyxMKi1_APMeUM8LBvGeqIL-d1qNMB9TpJlSc=w720-h300-no" alt="Git commit message and description" width="480" height="200" />

Finally, push your changes back to your repository with `git push`: 

<img src="https://lh3.googleusercontent.com/vXxa40em-Tbg0XunbSVqD7HEiqrNNlZJIb8UOOnN1ysfcY8KZH2USn1y1DxB-n8NAHRv1toM49Zvfe0v31HUUISGMcxQPNfbkK-avK8mqUqOkMz0MGjRSr5-nV1SDRuYcog51mTT1NBoI_U-M_KdxEI1U-_OWknEaIuLwAtWPkBW0N-eeDM--E4fO8dJXIX8eWk3z7PlR1urd8rOX9lJrUQpuKFsPx17wf0iO030JhO2Ddx4zsGr_i7yBwe97OSiRgRE37azLLprtGJmo_U3bMF-U5uzcGVLOND04WhSGWvzdKvK8TOOwX1yP4CcJT1BM9n_v9zWnBo16RQajcTL-OZC5Y5UwnZmlu6qJw_ORILWEQjDEdFSbaCERmWWfuqAAljg8rRHILPTpzKtQk0JhoRu28Il9WxnqMYocSkA5PtZI5DBZ4I4tHkNb2ChUopLPUUFkNAKv61Kl4SPEdPgKAc4fMbWJMxZKzjMQC22vphUFtk2hN_LwOectYVeB4n2CSo-Btm5cb1japg3Uv7EfhiuTjkFMOrsmxHy_nfncOzTUAqqijM6WJzC-XQgeIDxoZtOd2SS_3aXBYaW5XhIYaWtvf-46aUl-oJA60C9jI3ER03kCEboo2FxA8hwGgAp61qx-YfLDPpXWSETn5jaLGa3lHZyH3BLWMkpI60IB7pCK-RIVMK19Q4=w751-h301-no" alt="Using Git Push" width="480" height="205" />

## Review your changes on GitHub

Go back to your GitHub repository and refresh it. If you pushed your changes successfully, your repository will show your last commit, and it will be at least one commit ahead of the original lab's repository:

<img src="https://lh3.googleusercontent.com/W8b_pXqheF8fhTG1S_ApJwROqJqdSoLrfdueVCtRaI3YMuI50rr5gua18L1lPHbUHOJfn9jdUpgi44aq9WirSg0UOVMGrVpDMTGYpeesNDpV0QQeir2QOULq--WD5vcPgJUGX1BG6FXGmCA5cncOJqCzdI6uMaO55VQ0zSCqmIVsoapjCn27DcCjkxh_IvfCBfZmRgPI3ug9Dq2BzbA3s9af-d8r12HpGOpY9LXXaxJZwN-Ks9zf1QKQ8MZ5djXR-bklazUzWMNcosYHXlTDBJn8SGNGkrBcsM-jb7qCQnOoBjYatmmypROE6-l10FVZYHPv-UQeAKTqKM2nTgRLk3xrC48-wAmp_QLr0YRbVK4F3vWzTMJsl9psmrNt97Cdl9djGmyhc2kY3A16tA5EANfpC6Doz52Qc9cGKJRkhxiCFRr5rUvI_taIxV3j1jvJb6ToniSpsrfdDqhnduFuAhbCf00XxPA4qZE5B6X5XT62aE4utwBrNa5I_Ia788Rw75AMuUnJrL_Mtm-5ifVj2q0jBhGhqKug5qNI9-HuiKHB6FjyJ3Ir0AATDhE_g5BrF8oMzYvWHPBaA7t03AfKqj20FLxDrAWMHYiCXS7jUpE9938U1ZjPgSXXFA8Hzyr2GJ07eZS-k-sJ6YPZtEDtpWo07ewyScZe520K2iQJ5hRl7eqxVik-Sp8=w1131-h601-no" alt="GitHub repository with latest commit" width="565" height="300" />

Since we changed the README.md file, we can see our changes by scrolling down:

<img src="https://lh3.googleusercontent.com/3fer-w2ChvCL-iF0D-2Dd6JIGvxEmVMssLEbIfVsavvGQr_-zD-d7zQg5SMXOsFDWDVD12SOp-tK_QAEJqPmDgcEv24S8vg9tdESmVHbVY-ub80JtbvlBNkOxr1V87OtEn3Otf1ky1PLOYBkDBUjRfg8qCO5vvqSjGV7hA0ZB3l2zB6W7L8On_quSo5Rr6bfugevvqYeqVdNDHw7XLk51xlXlGSv305NBbPwJJIUj4BBHV3LTeafamUUqdP8vtSVwZzGcnNkfM08ClhgVQxhAW_w8YJUsH7vU3oJM9Egl7uV08MlfPZa6h3bVvpguFmJImZacXWDlvY8u1_0Cp_iY-ZmeqH4AfPkdK1ugxDn3JiyIUV7SJOQFq4jun_tUnKyf5X172u3bmit3iE3sV7EzMT5X7qn0YP8mSxxmUgoEIJBs7dea9y_uSmznCyeURv9akyHDuYruUCuiAxKT1_7xj7fSSauZJLEQKVAwqmHmpYHqQdAS2XtjN1so7HYJfYCnCAf0oAClCSp1EMwnEn7rffUobmeOxYdcqNqC_9uwrKGaPGb_mrkuU4WgimDZWu5vrOQq8T7rlz7BHd4rWqNhZz8XsdFox4uQqyRrU87TbicMQBvqSlq-_wYfNMUdT-JeZw23EBE0mrrNQNZzmbcEN7g-vc1ezjDpD3gKyQkrUORGILuiO-p8gs=w1091-h401-no" alt="Changes to Readme.md file" width="545" height="200" />

That looks good, so let's move onto the next step. If you want to change something else, then add, commit, and push your changes before coming back here.

## Open a Pull Request

We are finally ready to make a pull request! To do this, click on the **New pull request** button:

<img src="https://lh3.googleusercontent.com/GPPGoKaxcT9hALwHqJr6ZlngUTXWJWGT9e3KkYvkCc60CzlKPqw6ei5VVZdYj2y-fBVpnqhgY-pMNs30Y08xJ6xia3rpc2cOr0keJqLh0r-LmiMV4mtK7oLNmvi4TqDy-sxKwwZlH1heCTMsIP8I1_XdC3tuaiFobHjwE5gufGH6IKObl6oHKRPiweAIctLSDKdzTjzDi1DfgfLO5d4P5x5twQFSjgvqvU-P1ZPfeEgyk74u9G-EAxC-lV0L2GuYTW-Hjvmj9B0CpnzLKB9PGP8dLoscvFOJnD2ZAl_IRvpHHQ3vSTIaZtnOozZu07CD2X0VV1bjbDwrMEuRl-1Pq04cli--Jb8QJDKnXWlKMCeIPWfW0VDJQ_IBpbqWRTliR-QmyXInxciRje8d5N-SKAFN0JHuJw8SzcE-JQZqq_gm_J_jNYsDKMeqxQe1f8udjiJwKS0RZGosLrmSEVDZJN_ycdFluehdVzrElnVIe2KRwYs_foPzhoPWaWmHOxhzpk18yke3nGhcpUNhwL5J8d2_rN0HZFgugyN7K7ZZsx_0THHC2LV0Nxsd0sjHsXsIIsC-HaV0WL8PcWw6ZckxhaxEWcOH8fdi7X1nmwLAUKILDWiAZDRYFMn3JyTYZdHvK1CB7a3Y3SE9rCM-yJusRUXIBp_2gyEUaIV2yFdzZcdEvZs517Tbrr8=w1080-h326-no" alt="New pull request button" width="540" height="163" />

If your commits are able to merge, you should see a screen with a green **Create pull request** button. It will look something like this:

<img src="https://lh3.googleusercontent.com/Q9Rgqlm-xuftpLL1leVTNT5lY-cUjF1uHXbtRv8QLN2QpcLJTVhJPB6hDxR8r0jHcQW_1kIWb1mRUghG__ZJOxjAX42yYtE7v4oFyQ5PNcfJdnQgFNocNiHDCsTf-jkjprrYOgiWkjacL15I2jPIKEinSTgwerJKODZdh0wagcqoA8OpGn03uPSXoHxqSMrXKgAlk0SNxlV6q_j5oyqbGedq44-gJNv5PDnbB0EbUcC_p9LEvSSaKThYFgIFf65-eGBI-ue2FLzknIecmxWtIVeOtaIkpSgQV71MAZDDYLRDnz5C-IooTNjL763B2aOFAoLXEazaBCWWB222K6zNm_4NcCSEgvb54FKj71vBhLYoUOsSY3Uy_nNKJVORXTr0en5DGnvZzTlEQK-79bz1ROuriWkWsrLcdQgASQ2C-HkRMU2vSwOdi550xz6aKSll6vKIzxuJePlHw5c_EE_OsmN-KJ7KFmcgCih3zPbMqr77hkqEc69hNi8cMPy81t2JXQ08kDANpekQfJmvHDDIJ00x7X5-b5okuAYMmpGJrGeztnt5-GP6YsBpzlXFMi1eGh18oh6BgVU27ku0FrwvXECyLHBUndkEXpIc4RVW6byPk33t6PO4aZLwmmV67nkFdTPvDKVHAZMGvBF8YuMXoVfdxEGNmtHZM_bbbRPu0vz5vSH9GgBGjgY=w1540-h751-no" alt="Screen with 'Create Pull Request' button" width="616" height="300" />

When you click on that button, you'll be taken to the **Open a pull request** page. Here, you can review your commit and edit your commit message and description. Click the **Create pull request** button, and you're done!

<img src="https://lh3.googleusercontent.com/s3I8VMdIxeelKd8NOTa6O70RRPa8VlB-Z5GP_hMTgzP7nT6C8XyEamuG05w7hq1hzAxV3TX0BDO8deEjJjZ-jBdv0vSrYiD2-d6znnU7u_DP2aRw2utvDbMmOWmqp1MjIVHVafTuSSWWnrl7bfP3IL6EG_bhZT_aTcWAeByxikxmseqoOawYWvSGlr2adaR7On2dY09w5L9Hw9iHsXLXFGaOS8Iw4OMjlVfY9-3rikRKkQeU4oobyNyiU4qzXCm1LCBe-wDQ1URrvxNGO5OfGphr-MIJ6f04IQ4hVENQKZwlyiGFNKfhEzv247NgmauQGwhiLan6T8a5c6PDBQlJhXxL_z2C1Hi_D6-xz0Yv0MFUSXqUhY36aYHB1SNg9NDDt_VhJ6hPXsl76AakY7D6_hUussWnoKOKWs42Kf0z_G4cJgf-hLClIzqhkV8hioNbvMaCa5rnREsfyiaiu54q6UoSVBjv3IIcSJi2kV6W7ciE3clv1-AdHHu8murx8BTM6SsbmU-Z_hfM9QZfJeH7HaG6KCpTGOg0C-D9TroV-L4orx3nKYf04dIMiNTmAh08FMd-aIEp1pgot48145frXzQfAMhpn1_-73tONayZvM_KsTPyMfPYc8HZIGrsurhokkO6VfxMxARmGU_XXwr3Ec-XJqYrxJwe5wUvBE1j2dhfkASv06Xd2hw=w1101-h670-no" alt="Open a pull request" width="550" height="335" />

> **Side note:** Since this is just an example, I won't actually submit the pull request. The last thing I want to do is create a major headache for the Learn team!

If you're being *really* awesome by solving a raised issue with this pull request, go ahead and edit your commit description in the **Write** tab. Write something like "Fixes issue..." and paste in the URL of the raised issue. After you hit **Create pull request**, this will create a link to the raised issue on the pull request's page. (**Note:** I'm using a different example here, with an already-merged pull request for a closed issue.)

<img src="https://lh3.googleusercontent.com/vZZoN8D74KuTZ-NhJFb90kN4K2rvttaSsvkyb_nCxCbiMgxtnEFLyf7K7V6MHh0E0DYAWKm5ozxqasjtJe-37z5y__3-e7T4Bsr3FPHT-2EG_rc_MQNPEvJlavdkSMJOeROxtw4Q2dN5phI1aYhLZpVuWv-hcw1KuMesJfH2uWKja1KWcPjac1ODSInnBZ24OQTIUDDuQAImVx0JI6k4xYlnUr-FMbyf5zbFH5TXiZmqeHPkVBDZu0rEYN12FjRT-6nha1qn10QZfzp9leb3hXaSmqfETGeytBEDmNu-ZjErf1gEk2LcFNae8O1WTKmn7VL8ifATeBY2pe-JMq1gh0gK2AlykBZ1_nkEppDj6c4WUgFcjKoF5Z-VoOe0bm5HVotIPXVhEGj8RNYA0ANhZDySx3oFu0BNCQwat2irQW3oWYmRSRgWSLe3PoDPIgzYczdJWZJ1IbxBws8BHXCMUnPp84QjWqnStFtPutq9WdHN6YaNRXDgBHrNzNA13EleOAKmT3CvnLzgzkuV4Og8APJG0bOAAmIb36dcH6q48XItACLVfWRCGpkyh0oH0viZ4NgWKeFSJYj47gM2ck06hF_hXAzyhU1Lw4i0DK8r7aH7vAo-UeTfoZRoQgFvFy_YMe4Gr_IMqa7zIzhpbPEbQHogSGFqAeURJ9hbls18z2yyGQBqRCUPUos=w1100-h620-no" alt="Merged pull request referencing closed issue" width="550" height="310" />

It will also create a link to the pull request on the raised issue's page:

<img src="https://lh3.googleusercontent.com/MwtgRJMvzldfJBsO6zE-rFtmCrJbKx0Vkf8atCsD503sdfvWVdZWtZ943Ts4SKePPou9ihzfnfrrMUz4w6op45N0iNHBUZ22DXNRQVP2COhQoivare0BI_0MZ3DP6E4uTnKbaw2lkfK1anjezh1OY3K_Sq3A5TpGxA61_GRIb9nSIHJmMgGPv5bM2NsYDiBl4Ds5Z-At70ZfOHrsXIQHlYnGSnhhZ-APuILhicATeqQzrjQdIpbD-PVWsWi-u_6QIMgLGotSxjdmAcjP7DIuKdQrchzoTgQ_x7gEVrIJ2apTzWxHEatgdgGE_CC_avCxxVrmMd61UIUJmrovzJq5hqzhHHWyZdXIC5q4twjHB-JDl9yM8cbq5B0hJL5JoyLZj8GC5YqctikqX_gUSz5vE9oUisXm4mM_leMGjltdfaPtpx04fVCtE-hmZizFK1Y_mNJr4V8lu35wH0FTIgzLgpTk44pAVn9HjFRhDrKxfZbok8e2Jnc1tA4rcF6dn9kbCJa9d1JSIvGRmbcvx2oDfrUqRLaBIquehLT6oypJ5x1VwA9GJXNYpoHYzSsTewlMDu-0kK0s9jE1XZnSOicxVlq3eLCuivJd3qBnUmUDEKtMzR9YCW2qUimxEw5qB2lrY55hX8OltqIzKDlkD0JUWNSMtAkd8kmk5d04flYGqgI7UKB7RhEFG2A=w1100-h451-no" alt="Closed issue referenced by merged pull request" width="550" height="225" />

Cool! There's just *one* more thing that we may need to do.

## Make additional commits as needed

Suppose that you made a mistake with your pull request, or you've realized that you forgot to make an important change. What do you do, open another pull request? Thankfully, the answer is no. Just make a new commit, and push it to GitHub. That commit will be added to your pull request *automatically*.

**That's it!** Now you can make changes to any lesson/lab that you want! (But please make *good* changes; be nice to the Learn team.)

#### Hold up! Why would you want to do all of this in the first place? Why not just Raise an Issue?

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
