# Gender Bias in UCB Grad Admissions

`UCBAdmissions` dataset in base R. Female and male admitted or rejected from the 6 largest departments at Berkeley, 4526 students applied to Berkeley in 1973.
- 44.5% of male applicants were accepted into Berkeley, as opposed to 30.4% of female applicants

``gg_bar <- ucb_tidy_aggregated %>% 
    ggplot(aes(x = Gender, y = prop, fill = Gender)) +
    geom_col() +
    geom_text(aes(label = percent(prop)), vjust = -1) +
    labs(title = "Acceptance rate of male and female applicants",
         subtitle = "University of California, Berkeley (1973)",
         y = "Acceptance rate") +
    scale_y_continuous(labels = percent, limits = c(0, 0.5)) +
    guides(fill = FALSE)``

- Men were more likely to be admitted into Departments C and E, women were more likely to be admitted into the other departments
- 108 women, 825 men applied to Department A

``gg_bar_faceted <- ucb_by_dept %>% 
  ggplot(aes(Gender, prop, fill = Gender)) +
  geom_col() +
  geom_text(aes(label = percent(prop)), vjust = -1) +
  labs(title = "Acceptance rate of male and female applicants",
       subtitle = "University of California, Berkeley (1973)",
       y = "Acceptance rate") +
  scale_y_continuous(labels = scales::percent, limits = c(0, 1)) +
  facet_wrap(~Dept) +
  guides(fill=FALSE)``

- Simpson's paradox: effect of gender disappears when control for the effect of department on admission %. No campus-wide bias against applicants of either gender.
- bias != discrimination
