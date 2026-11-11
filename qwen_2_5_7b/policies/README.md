# Policies

| Policy | Abstain | Equivalent | Source |
|---|---|---|---|
| Abstain = tie | tie | tie | standard A/B/Tie |
| Drop Abstain | dropped | tie | common practice |
| λ-weighted tie | tie with weight λ (validated) | tie | interpolation baseline |
| IPW | dropped, similar pairs up-weighted | tie | inverse probability weighting |
| Human re-query | 20% sent to a random human, weight 1/ρ | tie | selective evaluation (Trust or Escalate) |
| Flip = tie (MT-Bench) | dropped | tie; A/B disagreement across orders = tie | Zheng et al., 2023 |
| Eq: half point | dropped | half a win each | Elo-style ties |
| Eq: drop ties | dropped | dropped | Bradley–Terry without ties |
| Soft labels | mass dropped | p(A), p(B), p(Eq) as soft outcomes | Soft-Elo, Conformal Elo (2606.13221) |
| Balanced position | dropped if averaged argmax is Abstain | probabilities averaged over both orders | Wang et al., 2023; TrustJudge (2509.21117) |


| Policy | Idea |
|---|---|
| Split Abstain | Abstain = tie with weight q(category), the human-tie share behind judge Abstains on J_cal |
| Flip = Abstain | A/B disagreement across orders means the judge could not decide: the pair is dropped, not tied |
| Split Equivalent | Equivalent = tie with weight q_E(category), the human-tie share behind judge Equivalents on J_cal; the rest is a soft win by p(A)/(p(A)+p(B)) averaged over orders |
| Hidden preference | Equivalent = soft win by p(A)/(p(A)+p(B)) averaged over orders; no tie |
| Uncertain = tie | A/B verdicts with a small margin \|p(A)−p(B)\|/(p(A)+p(B)) become ties; threshold validated on R (close to TrustJudge δ-tolerance) |
| Position correction | the judge's mean first-position shift in logits, estimated on J_cal, is subtracted before argmax (close to contextual calibration, Zhao et al., 2021) |
