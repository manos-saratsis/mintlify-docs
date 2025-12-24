I'll analyze the source code to create comprehensive documentation for billing and subscription management. Let me start by exploring the file system to understand the project structure and locate relevant files.

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp -type f -name "*.json" -o -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/tsconfig.json
/tmp/tmp_git_repo/package.json
/tmp/tmp_git_repo/tailwind.config.ts
/tmp/tmp_git_repo/next.config.ts
/tmp/tmp_git_repo/components.json
/tmp/tmp_git_repo/postcss.config.mjs
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">ls -la /tmp/tmp_git_repo/</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 164
drwxr-xr-x 11 sandbox sandbox  4096 Jan  8 22:37 .
drwxrwxrwt  1 root    root     4096 Jan  8 22:37 ..
drwxr-xr-x  8 sandbox sandbox  4096 Jan  8 22:37 .git
-rw-r--r--  1 sandbox sandbox   406 Jan  8 22:37 .gitignore
drwxr-xr-x  3 sandbox sandbox  4096 Jan  8 22:37 app
drwxr-xr-x  2 sandbox sandbox  4096 Jan  8 22:37 components
-rw-r--r--  1 sandbox sandbox   627 Jan  8 22:37 components.json
drwxr-xr-x  3 sandbox sandbox  4096 Jan  8 22:37 config
drwxr-xr-x  2 sandbox sandbox  4096 Jan  8 22:37 hooks
drwxr-xr-x  2 sandbox sandbox  4096 Jan  8 22:37 lib
-rw-r--r--  1 sandbox sandbox  1191 Jan  8 22:37 middleware.ts
-rw-r--r--  1 sandbox sandbox   314 Jan  8 22:37 next-env.d.ts
-rw-r--r--  1 sandbox sandbox   304 Jan  8 22:37 next.config.ts
drwxr-xr-x  3 sandbox sandbox  4096 Jan  8 22:37 node_modules
-rw-r--r--  1 sandbox sandbox  1577 Jan  8 22:37 package.json
-rw-r--r--  1 sandbox sandbox 86949 Jan  8 22:37 pnpm-lock.yaml
-rw-r--r--  1 sandbox sandbox   241 Jan  8 22:37 postcss.config.mjs
drwxr-xr-x  3 sandbox sandbox  4096 Jan  8 22:37 public
-rw-r--r--  1 sandbox sandbox   683 Jan  8 22:37 tailwind.config.ts
-rw-r--r--  1 sandbox sandbox   647 Jan  8 22:37 tsconfig.json
drwxr-xr-x  2 sandbox sandbox  4096 Jan  8 22:37 utils

</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -type f \( -name "*billing*" -o -name "*subscription*" -o -name "*payment*" -o -name "*stripe*" -o -name "*pricing*" \) | grep -E "\.(tsx?|jsx?|json)$"</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/app/(dashboard)/billing/page.tsx
/tmp/tmp_git_repo/config/subscriptions.ts

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/app/(dashboard)/billing/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { redirect } from "next/navigation";
import { getCurrentUser } from "@/lib/session";
import { getUserSubscriptionPlan } from "@/lib/subscription";
import { BillingForm } from "@/components/billing-form";
import { Alert, AlertDescription } from "@/components/ui/alert";
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@/components/ui/card";

export default async function BillingPage() {
  const user = await getCurrentUser();

  if (!user) {
    redirect("/login");
  }

  const subscriptionPlan = await getUserSubscriptionPlan(user.id);

  return (
    <div className="space-y-6">
      <div>
        <h1 className="text-3xl font-bold">Billing</h1>
        <p className="text-muted-foreground">
          Manage your subscription and billing information.
        </p>
      </div>

      <Alert>
        <AlertDescription>
          Your current plan is <strong>{subscriptionPlan.name}</strong>.
          {subscriptionPlan.isCanceled
            ? " Your plan will be canceled on "
            : subscriptionPlan.stripeCurrentPeriodEnd
            ? " Your plan renews on "
            : null}
          {subscriptionPlan.stripeCurrentPeriodEnd ? (
            <strong>
              {new Date(subscriptionPlan.stripeCurrentPeriodEnd).toLocaleDateString()}
            </strong>
          ) : null}
          .
        </AlertDescription>
      </Alert>

      <Card>
        <CardHeader>
          <CardTitle>Subscription Plan</CardTitle>
          <CardDescription>
            You are currently on the <strong>{subscriptionPlan.name}</strong> plan.
          </CardDescription>
        </CardHeader>
        <CardContent>
          <BillingForm
            subscriptionPlan={{
              ...subscriptionPlan,
              isCanceled: subscriptionPlan.isCanceled,
              stripeCurrentPeriodEnd: subscriptionPlan.stripeCurrentPeriodEnd,
            }}
          />
        </CardContent>
      </Card>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/config/subscriptions.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { SubscriptionPlan } from "@/types";

export const freePlan: SubscriptionPlan = {
  name: "Free",
  description: "The free plan is limited to 3 posts. Upgrade to the PRO plan for unlimited posts.",
  stripePriceId: "",
};

export const proPlan: SubscriptionPlan = {
  name: "PRO",
  description: "The PRO plan has unlimited posts.",
  stripePriceId: process.env.STRIPE_PRO_MONTHLY_PLAN_ID || "",
};
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo/components -name "*billing*" -type f</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/components/billing-form.tsx

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/components/billing-form.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
"use client";

import * as React from "react";
import { useRouter } from "next/navigation";
import { Button } from "@/components/ui/button";
import { toast } from "sonner";
import { SubscriptionPlan } from "@/types";

interface BillingFormProps {
  subscriptionPlan: SubscriptionPlan & {
    isCanceled: boolean;
    stripeCurrentPeriodEnd: number | null;
  };
}

export function BillingForm({ subscriptionPlan }: BillingFormProps) {
  const router = useRouter();
  const [isLoading, setIsLoading] = React.useState<boolean>(false);

  async function onSubmit(event: React.FormEvent) {
    event.preventDefault();
    setIsLoading(true);

    // Get a Stripe session URL.
    const response = await fetch("/api/users/stripe", {
      method: "POST",
    });

    if (!response?.ok) {
      toast.error("Something went wrong. Please refresh the page and try again.");
      setIsLoading(false);
      return;
    }

    // Redirect to the Stripe session.
    const session = await response.json();
    if (session) {
      window.location.href = session.url;
    }
  }

  return (
    <form onSubmit={onSubmit}>
      <div className="space-y-4">
        <div className="rounded-lg border p-4">
          <div className="flex justify-between items-start">
            <div>
              <h3 className="font-semibold">{subscriptionPlan.name}</h3>
              <p className="text-sm text-muted-foreground">
                {subscriptionPlan.description}
              </p>
            </div>
          </div>
        </div>

        <Button
          type="submit"
          disabled={isLoading}
          className="w-full"
        >
          {isLoading ? (
            "Loading..."
          ) : subscriptionPlan.stripePriceId ? (
            "Manage Subscription"
          ) : (
            "Upgrade to PRO"
          )}
        </Button>
      </div>
    </form>
  );
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -type f -name "*.ts" -o -name "*.tsx" | xargs grep -l "subscription" | grep -E "(lib|utils)" | head -10</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/lib/subscription.ts

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/lib/subscription.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { freePlan, proPlan } from "@/config/subscriptions";
import { db } from "@/lib/db";
import { UserSubscriptionPlan } from "@/types";

export async function getUserSubscriptionPlan(
  userId: string
): Promise<UserSubscriptionPlan> {
  const user = await db.user.findFirst({
    where: {
      id: userId,
    },
    select: {
      stripeSubscriptionId: true,
      stripeCurrentPeriodEnd: true,
      stripeCustomerId: true,
      stripePriceId: true,
    },
  });

  if (!user) {
    throw new Error("User not found");
  }

  // Check if user is on a pro plan.
  const isPro =
    user.stripePriceId &&
    user.stripeCurrentPeriodEnd &&
    user.stripeCurrentPeriodEnd.getTime() + 86_400_000 > Date.now();

  const plan = isPro ? proPlan : freePlan;

  return {
    ...plan,
    ...user,
    stripeCurrentPeriodEnd: user.stripeCurrentPeriodEnd?.getTime() || null,
    isPro: !!isPro,
    isCanceled: false,
  };
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo/app -type f -path "*/api/users/stripe*" | head -5</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/app/api/users/stripe/route.ts

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/app/api/users/stripe/route.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { getCurrentUser } from "@/lib/session";
import { stripe } from "@/lib/stripe";
import { getUserSubscriptionPlan } from "@/lib/subscription";
import { absoluteUrl } from "@/utils/absoluteUrl";

const billingUrl = absoluteUrl("/billing");

export async function POST() {
  try {
    const user = await getCurrentUser();

    if (!user || !user.id || !user.email) {
      return new Response("Unauthorized", { status: 401 });
    }

    const subscriptionPlan = await getUserSubscriptionPlan(user.id);

    // The user is on the pro plan.
    // Create a portal session to manage subscription.
    if (subscriptionPlan.isPro && subscriptionPlan.stripeCustomerId) {
      const stripeSession = await stripe.billingPortal.sessions.create({
        customer: subscriptionPlan.stripeCustomerId,
        return_url: billingUrl,
      });

      return new Response(JSON.stringify({ url: stripeSession.url }));
    }

    // The user is on the free plan.
    // Create a checkout session to upgrade.
    const stripeSession = await stripe.checkout.sessions.create({
      success_url: billingUrl,
      cancel_url: billingUrl,
      payment_method_types: ["card"],
      mode: "subscription",
      billing_address_collection: "auto",
      customer_email: user.email,
      line_items: [
        {
          price: process.env.STRIPE_PRO_MONTHLY_PLAN_ID,
          quantity: 1,
        },
      ],
      metadata: {
        userId: user.id,
      },
    });

    return new Response(JSON.stringify({ url: stripeSession.url }));
  } catch (error) {
    console.error(error);
    return new Response("Internal Server Error", { status: 500 });
  }
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -type f -name "*.ts" -o -name "*.tsx" | xargs grep -l "webhook" | head -5</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/app/api/webhooks/stripe/route.ts

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/app/api/webhooks/stripe/route.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
import Stripe from "stripe";
import { headers } from "next/headers";
import { db } from "@/lib/db";
import { stripe } from "@/lib/stripe";

export async function POST(req: Request) {
  const body = await req.text();
  const signature = headers().get("Stripe-Signature") as string;

  let event: Stripe.Event;

  try {
    event = stripe.webhooks.constructEvent(
      body,
      signature,
      process.env.STRIPE_WEBHOOK_SECRET || ""
    );
  } catch (error) {
    return new Response(`Webhook Error: ${error}`, { status: 400 });
  }

  const session = event.data.object as Stripe.Checkout.Session;

  if (event.type === "checkout.session.completed") {
    // Retrieve the subscription details from Stripe.
    const subscription = await stripe.subscriptions.retrieve(
      session.subscription as string
    );

    // Update the user stripe info in our database.
    await db.user.update({
      where: {
        id: session?.metadata?.userId,
      },
      data: {
        stripeSubscriptionId: subscription.id,
        stripeCustomerId: subscription.customer as string,
        stripePriceId: subscription.items.data[0].price.id,
        stripeCurrentPeriodEnd: new Date(
          subscription.current_period_end * 1000
        ),
      },
    });
  }

  if (event.type === "invoice.payment_succeeded") {
    // Retrieve the subscription details from Stripe.
    const subscription = await stripe.subscriptions.retrieve(
      session.subscription as string
    );

    // Update the price id and set the new period end.
    await db.user.update({
      where: {
        stripeSubscriptionId: subscription.id,
      },
      data: {
        stripePriceId: subscription.items.data[0].price.id,
        stripeCurrentPeriodEnd: new Date(
          subscription.current_period_end * 1000
        ),
      },
    });
  }

  return new Response(null, { status: 200 });
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -name "types*" -type f | head -5</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/types/index.ts

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/types/index.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">
export interface SubscriptionPlan {
  name: string;
  description: string;
  stripePriceId: string;
}

export interface UserSubscriptionPlan extends SubscriptionPlan {
  stripeSubscriptionId?: string | null;
  stripeCurrentPeriodEnd?: number | null;
  stripeCustomerId?: string | null;
  isPro: boolean;
  isCanceled: boolean;
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -type f -name "*.tsx" | xargs grep -l "navigation\|nav\|menu" | grep -E "(app|components)" | head -5</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/app/(dashboard)/layout.tsx
/tmp/tmp_git_repo/components/main-nav.tsx
/tmp/tmp_git_repo/components/user-nav.tsx

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/components/main-nav.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
"use client";

import * as React from "react";
import Link from "next/link";
import { usePathname } from "next/navigation";
import { cn } from "@/lib/utils";

export function MainNav() {
  const pathname = usePathname();

  return (
    <nav className="flex items-center space-x-4 lg:space-x-6">
      <Link
        href="/dashboard"
        className={cn(
          "text-sm font-medium transition-colors hover:text-primary",
          pathname === "/dashboard" ? "text-primary" : "text-muted-foreground"
        )}
      >
        Dashboard
      </Link>
      <Link
        href="/billing"
        className={cn(
          "text-sm font-medium transition-colors hover:text-primary",
          pathname === "/billing" ? "text-primary" : "text-muted-foreground"
        )}
      >
        Billing
      </Link>
    </nav>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/app/(dashboard)/layout.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { MainNav } from "@/components/main-nav";
import { UserNav } from "@/components/user-nav";

export default function DashboardLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div className="flex min-h-screen flex-col">
      <header className="sticky top-0 z-50 w-full border-b bg-background/95 backdrop-blur supports-[backdrop-filter]:bg-background/60">
        <div className="container flex h-14 items-center">
          <MainNav />
          <div className="ml-auto flex items-center space-x-4">
            <UserNav />
          </div>
        </div>
      </header>
      <main className="flex-1">
        <div className="container py-6">{children}</div>
      </main>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">grep -r "PRO\|Free" /tmp/tmp_git_repo/config/ 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/config/subscriptions.ts:  name: "Free",
/tmp/tmp_git_repo/config/subscriptions.ts:  description: "The free plan is limited to 3 posts. Upgrade to the PRO plan for unlimited posts.",
/tmp/tmp_git_repo/config/subscriptions.ts:  name: "PRO",
/tmp/tmp_git_repo/config/subscriptions.ts:  description: "The PRO plan has unlimited posts.",

</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -name "package.json" -type f -exec cat {} \;</parameter>
</invoke>
</function_calls>
<parameter name="output">
{
  "name": "nextjs-saas-starter",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "@prisma/client": "^5.22.0",
    "@radix-ui/react-alert-dialog": "^1.1.2",
    "@radix-ui/react-dialog": "^1.1.2",
    "@radix-ui/react-dropdown-menu": "^2.1.2",
    "@radix-ui/react-label": "^2.1.0",
    "@radix-ui/react-slot": "^1.1.0",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.1",
    "lucide-react": "^0.454.0",
    "next": "15.0.3",
    "next-auth": "^5.0.0-beta.25",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "sonner": "^1.7.1",
    "stripe": "^17.3.1",
    "tailwind-merge": "^2.5.4",
    "tailwindcss-animate": "^1.0.7"
  },
  "devDependencies": {
    "@types/node": "^20",
    "@types/react": "^19",
    "@types/react-dom": "^19",
    "eslint": "^8",
    "eslint-config-next": "15.0.3",
    "postcss": "^8",
    "prisma": "^5.22.0",
    "tailwindcss": "^3.4.1",
    "typescript": "^5"
  }
}
</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">ls -la /tmp/tmp_git_repo/app/(dashboard)/</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 16
drwxr-xr-x 4 sandbox sandbox 4096 Jan  8 22:37 .
drwxr-xr-x 3 sandbox sandbox 4096 Jan  8 22:37 ..
drwxr-xr-x 2 sandbox sandbox 4096 Jan  8 22:37 billing
drwxr-xr-x 2 sandbox sandbox 4096 Jan  8 22:37 dashboard

</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">/tmp/tmp_git_repo/app/(dashboard)/dashboard/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">
import { redirect } from "next/navigation";
import { getCurrentUser } from "@/lib/session";
import { getUserSubscriptionPlan } from "@/lib/subscription";
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from "@/components/ui/card";

export default async function DashboardPage() {
  const user = await getCurrentUser();

  if (!user) {
    redirect("/login");
  }

  const subscriptionPlan = await getUserSubscriptionPlan(user.id);

  return (
    <div className="space-y-6">
      <div>
        <h1 className="text-3xl font-bold">Dashboard</h1>
        <p className="text-muted-foreground">
          Welcome back, {user.name || user.email}!
        </p>
      </div>

      <Card>
        <CardHeader>
          <CardTitle>Your Plan</CardTitle>
          <CardDescription>
            You are currently on the <strong>{subscriptionPlan.name}</strong> plan.
          </CardDescription>
        </CardHeader>
        <CardContent>
          <p className="text-sm text-muted-foreground">
            {subscriptionPlan.description}
          </p>
        </CardContent>
      </Card>
    </div>
  );
}
</parameter>

Now let me check for any additional billing or pricing-related pages:

<function_calls>
<invoke name="execute_shell">
<parameter name="command">find /tmp/tmp_git_repo -type f \( -name "*.tsx" -o -name "*.ts" \) | xargs grep -l "checkout\|portal\|payment" | head -10</parameter>
</invoke>
</function_calls>
<parameter name="output">
/tmp/tmp_git_repo/app/api/users/stripe/route.ts

</parameter>

<function_calls>
<invoke name="execute_shell">
<parameter name="command">mkdir -p /tmp/tmp_git_repo/user-facing-docs</parameter>
</invoke>
</function_calls>
<parameter name="output">
</parameter>

Now I'll create the comprehensive billing and subscription management tutorial based on the actual code:

<function_calls>
<invoke name="execute_shell">
<parameter name="command">cat > /tmp/tmp_git_repo/user-facing-docs/nextjs-saas-starter-billing-tutorial.md << 'EOF'
# Managing Your Subscription and Billing

This tutorial will walk you through everything you need to know about managing your subscription, upgrading your plan, and handling your billing information.

## Understanding Your Subscription Plans

The application offers two subscription tiers:

**Free Plan**
- Limited to 3 posts
- Perfect for trying out the service
- No credit card required

**PRO Plan**
- Unlimited posts
- Full access to all features
- Monthly subscription

## Getting Started with Billing

### Viewing Your Current Plan

When you first sign in, you'll see information about your current plan on the Dashboard page. This shows you which plan you're on and a brief description of what's included.

To access detailed billing information:

1. Look at the top navigation menu after signing in
2. Click on "Billing" in the menu
3. You'll see your complete billing information

### What You'll See on the Billing Page

The Billing page displays:

- **Your current plan name** (Free or PRO)
- **Plan renewal date** - When your subscription will renew (for PRO users)
- **Cancellation status** - If you've cancelled, when your access will end
- **Plan details** - A description of what's included in your plan
- **Action button** - Either "Upgrade to PRO" or "Manage Subscription"

## Upgrading from Free to PRO

### Step-by-Step Upgrade Process

1. **Navigate to the Billing page** using the menu at the top
2. **Review your current plan** displayed in the information box at the top
3. **Click the "Upgrade to PRO" button** at the bottom of the page
4. You'll be redirected to a secure payment page to enter your card details
5. Fill in your payment information and complete the purchase
6. After successful payment, you'll be brought back to the Billing page
7. Your plan will now show as "PRO" with your renewal date

### What Happens After Upgrading

-